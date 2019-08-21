+++
title = "OrderFraudCheck"
toc = true
+++

Run a fraud check on a passed Order ID using the active fraud module.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "OrderFraudCheck" | Required |
| orderid | int | The order id to complete the fraud check on | Required |
| ipaddress | string | To override the IP address on the fraud check | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| status | string | The status of the fraud check |
| module | string | The module loaded to complete the fraud check |
| results | string | The serialised results of the fraud check |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'OrderFraudCheck',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'orderid' => '1',
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
$command = 'OrderFraudCheck';
$postData = array(
    'orderid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "module": "maxmind",
    "status": "Pass"
}
```


### Error Responses

Possible error condition responses include:

* Order ID Not Found
* No Active Fraud Module


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
