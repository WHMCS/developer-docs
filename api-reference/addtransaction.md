+++
title = "AddTransaction"
toc = true
+++

Add a transaction to the system

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddTransaction" | Required |
| paymentmethod | string | The payment method of the transaction in system format | Required |
| userid | int | The ID of the user to apply the transaction to | Optional |
| invoiceid | int | The ID of the invoice the transaction is for | Optional |
| transid | string | The unique transaction id for this payment | Optional |
| date | string | The date of the transaction in your Localisation Format (eg DD/MM/YYYY) | Optional |
| currencyid | int | The currency id for the transaction if not associated with a user | Optional |
| description | string | The description of the transaction | Optional |
| amountin | float | The amount received by the payment | Optional |
| fees | float | The amount of fee charged on the transaction by the merchant - This can be negative | Optional |
| amountout | float | The amount paid out by the payment | Optional |
| rate | float | The exchange rate for the payment based on the default currency | Optional |
| credit | bool | Should the payment be applied to credit on the client account. Invoice ID must not be provided. | Optional |
| allowduplicatetransid | bool | Should an already existing transaction id be allowed. Defaults to false. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddTransaction',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'paymentmethod' => 'paypal',
            'userid' => '1',
            'transid' => 'FJWEK32DWO329JFW',
            'date' => '01/01/2016',
            'description' => 'A sample API payment',
            'amountin' => '10.00',
            'fees' => '0.89',
            'rate' => '1.00000',
            'responsetype' => 'json',
        )
    )
);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddTransaction';
$postData = array(
    'paymentmethod' => 'paypal',
    'userid' => '1',
    'transid' => 'FJWEK32DWO329JFW',
    'date' => '01/01/2016',
    'description' => 'A sample API payment',
    'amountin' => '10.00',
    'fees' => '0.89',
    'rate' => '1.00000',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* Invoice ID Not Found
* User ID does not own the given Invoice ID
* Currency ID Not Found
* Currency ID does not match Client currency
* A Currency ID is required for non-customer related transactions
* Payment Method is required
* Transaction ID must be Unique


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
