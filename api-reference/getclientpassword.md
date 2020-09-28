+++
title = "GetClientPassword"
toc = true
+++

Obtain the encrypted client password

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientPassword" | Required |
| userid | int | The userid to obtain the password for | Optional |
| email | string | The email address to obtain the password for | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| password | string | The clients encrypted password |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientPassword',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'userid' => '1',
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
$command = 'GetClientPassword';
$postData = array(
    'userid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "password": "$2y$10$17X1fBPpamALcMA9KMiFneH4FYpMkkmFGDxlkxbjGeSnfH8sLqixa"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.0 | Deprecated. |
