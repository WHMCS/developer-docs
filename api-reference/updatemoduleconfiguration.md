+++
title = "UpdateModuleConfiguration"
toc = true
+++

Activates a given module.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateModuleConfiguration" | Required |
| moduleType | string | The module type to be activated | Required |
| moduleName | string | The module name to be activated | Required |
| parameters | array | An array of configuration parameters to set for the given module. Use *GetModuleConfigurationParameters* to obtain a list of fields for a given module. | Optional |

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
            'action' => 'UpdateModuleConfiguration',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'moduleType' => 'gateway',
            'moduleName' => 'paypal',
            'parameters[email]' => 'billing@example.com',
            'parameters[forcesubscriptions]' => 'true',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'UpdateModuleConfiguration';
$postData = array(
    'moduleType' => 'gateway',
    'moduleName' => 'paypal',
    'parameters[email]' => 'billing@example.com',
    'parameters[forcesubscriptions]' => 'true',
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
* Module activation not supported by module type.
* Module Configuration Update Failed: xxx
* An unexpected error occurred: xxx


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.0.0-beta.1 | Initial Version |
