+++
title = "AddInvoicePayment"
toc = true
+++

Adds payment to a given invoice.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddInvoicePayment" | Required |
| invoiceid | int |  | Required |
| transid | string | The unique transaction id that should be applied to the payment | Required |
| gateway | string | the gateway used in system name format, eg. paypal, authorize | Required |
| date | \Carbon\Carbon | The date that the payment should have assigned. Format: YYYY-MM-DD HH:mm:ss | Optional |
| amount | float | the amount paid, can be left undefined to take full amount of invoice | Optional |
| fees | float | the amount of the payment that was taken as a fee by the gateway | Optional |
| noemail | bool | set to true to not send an email for the invoice payment | Optional |

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
            'action' => 'AddInvoicePayment',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'invoiceid' => '1',
            'transid' => 'D28DJIDJW393JDWQKQI332',
            'gateway' => 'mailin',
            'date' => '2016-01-01 12:33:12',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddInvoicePayment';
$postData = array(
    'invoiceid' => '1',
    'transid' => 'D28DJIDJW393JDWQKQI332',
    'gateway' => 'mailin',
    'date' => '2016-01-01 12:33:12',
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

* Invoice ID Not Found
* It is not possible to add a payment to an invoice that is Cancelled


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
