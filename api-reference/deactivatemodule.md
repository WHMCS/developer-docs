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
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'moduleType' => 'gateway',
            'moduleName' => 'paypal',
            'responsetype' => 'json',
        )
    )
);
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

* Invalid module type provided. Supported module types include: xxx
* Invalid module name provided.
* Module deactivation not supported by module type.
* Failed to deactivate: xxx
* An unexpected error occurred: xxx


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.0.0-beta.1 | Initial Version |
