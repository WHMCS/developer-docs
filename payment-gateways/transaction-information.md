+++
next = "/payment-gateways/callbacks"
prev = "/payment-gateways/displaying-balances"
title = "Transaction Information"
toc = true
weight = 56

+++

WHMCS 8.2 added the ability to display additional transaction details in a modal in the WHMCS Admin Area. Clicking on a transaction ID will open the modal to display this information for enabled supported gateways. By default, these details are available by clicking a transaction ID at **Billing > Transactions**.

All Stripe gateways support this by default. You can display transaction information for other gateways using the `TransactionInformation` function.

## Displaying Transaction Information

The following example code connects to the gateway and displays the transaction information:

```
use WHMCS\Billing\Payment\Transaction\Information;
use WHMCS\Carbon;

/**
 * @param array @params
 *
 * @return Information
 */
function yourmodulename_TransactionInformation(array $params = []): Information
{
    /**
     * Connect to gateway to retrieve transaction information.
     */
    $postfields = [
        'account' => $params['apikey'],
        'transactionId' => $params['transactionId'],
    ];
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/transaction');
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    $transactionInformation = json_decode($response);
    return (new Information())
        ->setTransactionId($transactionData['id'])
        ->setAmount($transactionData['amount'])
        ->setCurrency($transactionData['currency'])
        ->setType($transactionData['type'])
        ->setAvailableOn(Carbon::parse($transactionData['available_on']))
        ->setCreated(Carbon::parse($transactionData['created']))
        ->setDescription($transactionData['description'])
        ->setFee($transactionData['fee'])
        ->setStatus($transactionData['status'])
        ->setAdditionalDatum('customName1', $transactionData['customValue1'])
        ->setAdditionalDatum('customName2', $transactionData['customValue2']);
}
```

## The Information Class

The use of the `Information` class causes the return from the `TransactionInformation` function to be standard.

This class has no attribute requirements, but we recommend that you set `id`, `amount`, and `currency` as in the example above. The data that you set here determines what displays in the modal. Values that evaluate to false will not display in the modal.

For more information about the `Information` class, see the [WHMCS Internal Class Documentation](https://classdocs.whmcs.com/).

### Setting Additional Data

Use the `Information` class's `setAdditionalDatum` method to add data. The passed value will display with the label for the key. For example:

```
setAdditionalDatum(string $key, $value)
```

### key Language String Override

The `key` value will be translated before it displays in the modal. You will need to add an [admin language string override](/languages/overrides/) for each additional piece of data.

For the code example above, you would add the following language strings:

```
$_ADMINLANG['transactions']['information']['customName1'] = "Custom Name 1";
$_ADMINLANG['transactions']['information']['customName2'] = "Custom Name 2";
```

## Required Permissions

By default, transaction information will display in the Admin Area for admins with the **Full Administrator** role. To allow other admin roles to see balance information, enable **List Transactions** for the desired role.
