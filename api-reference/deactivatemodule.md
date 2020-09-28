+++
title = "DeactivateModule"
toc = true
+++

Deactivates a given module.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DeactivateModule" | Required |
| moduleType | string | The module type to be deactivated | Required |
| moduleName | string | The module name to be deactivated | Required |
| newGateway | string | The Gateway to switch respective entities to when deactivating a Gateway Module. | Optional |

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
            'action' => 'DeactivateModule',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'moduleType' => 'gateway',
            'moduleName' => 'paypal',
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
$command = 'DeactivateModule';
$postData = array(
    'moduleType' => 'gateway',
    'moduleName' => 'paypal',
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

* Invalid module type provided. Supported module types include: xxx
* Invalid module name provided.
* Module deactivation not supported by module type.
* Failed to deactivate: xxx
* An unexpected error occurred: xxx


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.0.0-beta.1 | Initial Version |
