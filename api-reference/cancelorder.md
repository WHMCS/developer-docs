+++
title = "CancelOrder"
toc = true
+++

Cancel a Pending Order

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CancelOrder" | Required |
| orderid | int | The ID of the pending order | Required |
| cancelsub | bool | Attempt to cancel the subscription associated with the products | Optional |
| noemail | bool | Set to true to stop the invoice payment email being sent if the invoice becomes paid | Optional |

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
            'action' => 'CancelOrder',
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
$command = 'CancelOrder';
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
    "result": "success"
}
```


### Error Responses

Possible error condition responses include:

* Order ID not found or Status not Pending
* Subscription Cancellation Failed - Please check the gateway log for further information


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
