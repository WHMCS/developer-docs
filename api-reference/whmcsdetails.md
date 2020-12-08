+++
title = "WhmcsDetails"
toc = true
+++

Obtain details pertaining to the current WHMCS installation

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "WhmcsDetails" | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| whmcs | array | The version details of the current WHMCS installation |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'WhmcsDetails',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
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
$command = 'WhmcsDetails';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "whmcs": {
        "version": "8.0.0",
        "canonicalversion": "8.0.0-release.1"
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 8.0.0 | Initial Version |
