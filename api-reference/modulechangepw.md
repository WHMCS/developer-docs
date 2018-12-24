+++
title = "ModuleChangePw"
toc = true
+++

Runs a change password action for a given service.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "ModuleChangePw" | Required |
| serviceid | int | The service ID to run the action for | Required |
| servicepassword | string | A new password to assign to the service | Optional |

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
            'action' => 'ModuleChangePw',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'serviceid' => '1',
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
$command = 'ModuleChangePw';
$postData = array(
    'serviceid' => '1',
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

* Service ID is required
* Service ID not found
* Service not assigned to a module
* Server response message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Renamed `accountid` parameter to `serviceid`. Backwards compatibility preserved for `accountid`. |
