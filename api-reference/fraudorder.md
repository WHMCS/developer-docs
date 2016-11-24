+++
title = "FraudOrder"
toc = true
+++

Marks an order as fraudulent.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "FraudOrder" | Required |
| orderid | int | The Order ID to set as fraud | Required |
| cancelsub | bool | Pass as true to cancel any PayPal Subscription(s) associated with the products & services that belong to the given order. | Optional |

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
            'action' => 'FraudOrder',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'orderid' => '1',
            'cancelsub' => '1',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'FraudOrder';
$postData = array(
    'orderid' => '1',
    'cancelsub' => '1',
);
$adminUsername = 'ADMIN_USERNAME';

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

* Order ID Not Found
* Subscription Cancellation Failed - Please check the gateway log for further information


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
