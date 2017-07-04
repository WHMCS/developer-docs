+++
title = "UpdateTransaction"
toc = true
+++

Updates a transaction in the system

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateTransaction" | Required |
| transactionid | int | The unique id of the transaction to update | Required |
| refundid | int | The unique id of the transaction that this transaction refunds | Optional |
| userid | int | The ID of the user to apply the transaction to | Optional |
| invoiceid | int | The ID of the invoice the transaction is for | Optional |
| transid | string | The unique transaction id for this payment | Optional |
| date | \Carbon\Carbon | The date of the transaction Y-m-d | Optional |
| gateway | string | The gateway of the transaction in system format | Optional |
| currency | int | The currency id for the transaction if not associated with a user | Optional |
| description | string | The description of the transaction | Optional |
| amountin | float | The amount received by the payment | Optional |
| fees | float | The amount of fee charged on the transaction by the merchant - This can be negative | Optional |
| amountout | float | The amount paid out by the payment | Optional |
| rate | float | The exchange rate for the payment based on the default currency | Optional |
| credit | bool | Should the payment be applied to credit on the client account. Invoice ID must not be provided. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| transactionid | int | The id of the updated transaction |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateTransaction',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'transactionid' => '1',
            'transid' => 'FJWEK32DWO329JFWUPDATE',
            'rate' => '1.00000',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'UpdateTransaction';
$postData = array(
    'transactionid' => '1',
    'transid' => 'FJWEK32DWO329JFWUPDATE',
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


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
