+++
title = "DeleteClient"
toc = true
+++

Deletes a client.

Removes client record and all associated data. This action cannot be undone.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DeleteClient" | Required |
| clientid | int | The client id to be deleted | Required |
| deleteusers | bool | Delete any users not associated with any other client. | Optional |
| deletetransactions | bool | Delete all transactions on this account | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| clientid | int | The client id that was deleted |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'DeleteClient',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'deleteusers' => false,
            'deletetransactions' => true,
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
$command = 'DeleteClient';
$postData = array(
    'clientid' => '1',
    'deleteusers' => false,
    'deletetransactions' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "clientid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* Client Delete Failed: xxxxxx


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
