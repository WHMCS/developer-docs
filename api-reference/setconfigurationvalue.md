+++
title = "SetConfigurationValue"
toc = true
+++

Set a System Configuration Value via the local API only.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "SetConfigurationValue" | Required |
| setting | string | The setting name to change | Required |
| value | string | The value to set. Leave value blank to unset. | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| value_changed | bool | Confirmation that the value was changed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'SetConfigurationValue',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'setting' => 'PremiumDomains',
            'value' => '',
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
$command = 'SetConfigurationValue';
$postData = array(
    'setting' => 'PremiumDomains',
    'value' => '',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "value_changed": "true"
}
```


### Error Responses

Possible error condition responses include:

* Parameter setting is required
* Invalid name for parameter setting
* Parameter value is required


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
