+++
title = "AddUser"
toc = true
+++

Add a user.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddUser" | Required |
| firstname | string |  | Required |
| lastname | string |  | Required |
| email | string |  | Required |
| password2 | string | The password for the newly created user account | Required |
| language | string | Default language setting. Provide full name: 'english', 'french', etc... | Optional |

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
            'action' => 'AddUser',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'firstname' => 'John',
            'lastname' => 'Doe',
            'email' => 'john.doe@example.com',
            'password2' => 'password',
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
$command = 'AddUser';
$postData = array(
    'firstname' => 'John',
    'lastname' => 'Doe',
    'email' => 'john.doe@example.com',
    'password2' => 'password',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "user_id": "1"
}
```


### Error Responses

Possible error condition responses include:

* You did not enter a first name
* You did not enter a last name
* You did not enter an email address
* You did not enter a password
* The email address entered is not valid
* A user already exists with that email address


### Version History

| Version | Changelog |
| ------- | --------- |
| 8.0.0 | Initial Version |
