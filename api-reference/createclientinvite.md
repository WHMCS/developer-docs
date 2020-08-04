+++
title = "CreateClientInvite"
toc = true
+++

Send an invite to manage a client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateClientInvite" | Required |
| email | int | The email address to invite | Required |
| client_id | string | The ID of the client the invite is for | Required |
| permissions | string | A comma separated list of permissions. | Required |

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
            'action' => 'CreateClientInvite',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'user_id' => '1',
            'firstname' => 'John',
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
$command = 'CreateClientInvite';
$postData = array(
    'user_id' => '1',
    'firstname' => 'John',
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

* Email is required
* Invalid client id
* The email address entered is not valid
* User permissions are required
* User already associated with client


### Version History

| Version | Changelog |
| ------- | --------- |
| 8.0.0 | Initial Version |
