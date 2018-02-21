+++
title = "GetModuleConfigurationParameters"
toc = true
+++

Obtains the Module Configuration Parameters

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetModuleConfigurationParameters" | Required |
| moduleType | string | The module type to be activated | Required |
| moduleName | string | The module name to be activated | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| parameters | array | An array of configuration parameters available to be set for the given module. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetModuleConfigurationParameters',
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
$command = 'GetModuleConfigurationParameters';
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
    "result": "success",
    "parameters[0][name]": "FriendlyName",
    "parameters[0][displayName]": "FriendlyName",
    "parameters[0][fieldType]": "text",
    "parameters[1][name]": "email",
    "parameters[1][displayName]": "PayPal Email",
    "parameters[1][fieldType]": "text",
    "parameters[2][name]": "forceonetime",
    "parameters[2][displayName]": "Force One Time Payments",
    "parameters[2][fieldType]": "yesno",
    "parameters[3][name]": "forcesubscriptions",
    "parameters[3][displayName]": "Force Subscriptions",
    "parameters[3][fieldType]": "yesno",
    "parameters[4][name]": "requireshipping",
    "parameters[4][displayName]": "Require Shipping Address",
    "parameters[4][fieldType]": "yesno",
    "parameters[5][name]": "overrideaddress",
    "parameters[5][displayName]": "Client Address Matching",
    "parameters[5][fieldType]": "yesno",
    "parameters[6][name]": "apiusername",
    "parameters[6][displayName]": "API Username",
    "parameters[6][fieldType]": "text",
    "parameters[7][name]": "apipassword",
    "parameters[7][displayName]": "API Password",
    "parameters[7][fieldType]": "text",
    "parameters[8][name]": "apisignature",
    "parameters[8][displayName]": "API Signature",
    "parameters[8][fieldType]": "text",
    "parameters[9][name]": "sandbox",
    "parameters[9][displayName]": "Sandbox Mode",
    "parameters[9][fieldType]": "yesno"
}
```


### Error Responses

Possible error condition responses include:

* Invalid module type provided. Supported module types include: xxx
* Invalid module name provided.
* Get module configuration parameters not supported by module type.
* An unexpected error occurred: xxx


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.0.0-beta.1 | Initial Version |
