+++
title = "GetAdminUsers"
toc = true
+++

Retrieve a list of administrator user accounts.

phpcs:disable

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetAdminUsers" | Required |
| roleid | int | An administrative role ID to filter for. | Optional |
| email | string | An email address to filter for. Partial matching supported. | Optional |
| include_disabled | bool | Pass as true to include disabled administrator user accounts in response. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| count | int | Total number of administrative users matching supplied criteria. |
| admin_users | array | An array of administrator users and their attributes. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetAdminUsers',
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
$command = 'GetAdminUsers';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
null
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.7 | Initial Version |
