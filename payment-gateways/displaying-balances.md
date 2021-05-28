+++
next = "/payment-gateways/callbacks"
prev = "/payment-gateways/merchant-gateway"
title = "Displaying Balances"
toc = true
weight = 55

+++

WHMCS 8.2 adds the ability to display payment gateway balances directly in the WHMCS Admin Area. By default, these balances are available for Stripe and PayPal Basic at **Billing > Transactions**.

By default, balance information will display in the Admin Area for admins with the **Full Administrator** role. To allow other admin roles to see balance information, enable **View Gateway Balances** for the desired role.

You can display the balances for other payment gateways through two payment gateway module classes: `BalanceInterface` and `BalanceCollection`.

## Example

Successful implementations of this functionality within a payment gateway module should resemble the example below:

```
use WHMCS\Module\Gateway\Balance;
use WHMCS\Module\Gateway\BalanceCollection;

/**
 * @param array $params
 *
 * @return BalanceCollection
 */
function yourmodulename_account_balance(array $params = []): BalanceCollection
{
    $balanceInfo = [];
    /**
     * Connect to gateway to retrieve balance information.
     */
    $postfields = [
        'account' => $params['apikey'],
    ];
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/balance');
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    $balanceData = json_decode($response);

    /**
     * Add Balance objects as many times as needed for each gateway
     * balance type (most gateways will only have one).
     */
    foreach ($balanceData['available'] as $availableData) {
        $currencyCode = strtoupper($availableData['currency']);
        $amount[$currencyCode] = ($availableData['amount'] / 100);

        /**
         * Add a Balance object using the default label and format color.
         */
        $balanceInfo[] = Balance::factory(
            $amount[$currencyCode],
            $currencyCode
        );
    }

    foreach ($balanceData['pending'] as $pendingData) {
        $currencyCode = strtoupper($pendingData['currency']);
        $pending[$currencyCode] = ($pendingData['amount'] / 100);

        /**
         * Add a Balance object overriding the default label and color.
         */
        $balanceInfo[] = Balance::factory(
            $pending[$currencyCode],
            $currencyCode,
            'status.pending', //The default label is status.available.
            '#6ecacc' //The default color hex code is #5dc560.
        );
    }

    /**
     * The BalanceCollection object accepts an array containing any number of
     * Balance objects. Passing an item in the array that is not a Balance
     * object will cause a fatal error.
     */
    return BalanceCollection::factoryFromItems(...$balanceInfo);
}
```
