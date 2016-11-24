+++
title = "ValidateLogin"
toc = true
+++

Validate client login credentials.

This command can be used to validate an email address and password against
a registered user in WHMCS. On success, the userid and password hash will
be returned which can be used to create an authenticated session.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "ValidateLogin" | Required |
| email | string | Client or Sub-Account Email Address | Required |
| password2 | string | Password to validate | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| userid | int | Client ID |
| contactid | int | Contact ID if credentials match with a Sub-Account |
| passwordhash | string | Password hash |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'ValidateLogin',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'email' => 'user@example.com',
            'password2' => 'abc123',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'ValidateLogin';
$postData = array(
    'email' => 'user@example.com',
    'password2' => 'abc123',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "userid": "1",
    "passwordhash": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```


### Error Responses

Possible error condition responses include:

* Email or Password Invalid


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
