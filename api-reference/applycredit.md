+++
title = "ApplyCredit"
toc = true
+++

Applies the Client's Credit to an invoice

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "ApplyCredit" | Required |
| invoiceid | int | The ID of the invoice to apply credit | Required |
| amount | float\|string | The amount of credit to apply to the invoice. | Optional |
| noemail | bool | Set to true to stop the invoice payment email being sent if the invoice becomes paid | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| invoiceid | int | The id of the invoice the credit has been applied to |
| amount | float | The amount of credit applied |
| invoicepaid | string | true/false string |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'ApplyCredit',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'invoiceid' => '1',
            'amount' => '10.00',
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
$command = 'ApplyCredit';
$postData = array(
    'invoiceid' => '1',
    'amount' => '10.00',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "invoiceid": "1",
    "amount": "10.00",
    "invoicepaid": "false"
}
```


### Error Responses

Possible error condition responses include:

* Invoice ID Not Found
* Invoice Not in Unpaid Status
* Amount exceeds customer credit balance
* Amount Exceeds Invoice Balance
* Credit Amount to apply must be greater than zero


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
