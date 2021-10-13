+++
next = "/payment-gateways/transaction-information"
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
You can display the balances for other payment gateways through two payment gateway module classes: `BalanceInterface` and `BalanceCollection`.

## Connecting to Gateways

Before you can retrieve balance information, connect to the desired gateway. For example:

```
<?php

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

    // Connect to gateway to retrieve balance information.
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

    $balanceData = json_decode($response, true);

    // Add Balance objects as many times as needed for each gateway
    // balance type (most gateways will only have one).
    foreach ($balanceData['available'] as $availableData) {
        $currencyCode = strtoupper($availableData['currency']);
        $amount[$currencyCode] = ($availableData['amount'] / 100);

        // Add a Balance object using the default label and format color.
        $balanceInfo[] = Balance::factory(
            $amount[$currencyCode],
            $currencyCode
        );
    }

    foreach ($balanceData['pending'] as $pendingData) {
        $currencyCode = strtoupper($pendingData['currency']);
        $pending[$currencyCode] = ($pendingData['amount'] / 100);

        // Add a Balance object overriding the default label and color.
        $balanceInfo[] = Balance::factory(
            $pending[$currencyCode],
            $currencyCode,
            'status.pending', //The default label is status.available.
            '#6ecacc' //The default color hex code is #5dc560.
        );
    }

    // The BalanceCollection object accepts an array containing any number of
    // Balance objects. Passing an item in the array that is not a Balance
    // object will cause a fatal error.
    return BalanceCollection::factoryFromItems(...$balanceInfo);
}
```

## The Balance Class

After you connect to the gateway, add an object for the `Balance` class.

You can repeat this process as many times as needed for each balance type that the gateway supports (for example, *Available* and *Pending*). However, most gateways will only have one `Balance` type.

You can do this in two ways:

### Using the default label and color

{{% notice info %}}
You must add an object for the `Balance` class using this method **at least** once.
{{% /notice %}}

```
foreach ($balanceData['available'] as $availableData) {
    $currencyCode = strtoupper($availableData['currency']);
    $amount[$currencyCode] = ($availableData['amount'] / 100);

    // Add a Balance object using the default label and format colour.
    $balanceInfo[] = Balance::factory(
        $amount[$currencyCode],
        $currencyCode
    );
}
```

### Overriding the label and color

Adding an object that overrides the label, color, or both is optional. To override the label and color, add the desired label and hex color code as in the example below:

```
$balanceInfo[] = Balance::factory(
    $pending[$currencyCode],
    $currencyCode,
    'status.pending', // Default label is 'status.available'
    '#6ecacc' //default colour is #5dc560
);
```

## The BalanceCollection Class

Next, add an object to the `BalanceCollection` class. It should accept an array of `Balance` objects.

{{% notice info %}}
If anything in the array **isn't** a `Balance` object, WHMCS will encounter a fatal error.
{{% /notice %}}

```
// The BalanceCollection object accepts an array containing any number of Balance objects.
// Passing an item in the array that is not a Balance object will cause a fatal error.
return BalanceCollection::factoryFromItems(...$balanceInfo);
```

## Required Permissions

By default, balance information will display in the Admin Area for admins with the **Full Administrator** role. To allow other admin roles to see balance information, enable **View Gateway Balances** for the desired role.
