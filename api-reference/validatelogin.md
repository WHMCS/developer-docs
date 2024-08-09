+++
title = "ValidateLogin"
toc = true
+++

This command can be used to validate an email address and password against a registered user in WHMCS.

If the email address is valid, and the password is correct, a session will be started as part of creating
a passwordhash. This session can be used for remote sign-in, (see below) but can affect other aspects of
your script if using the LocalAPI. A validated login will update the last login time stored for the
client account. On success, the `userid` and `passwordhash` will be returned. This can be used to establish
an authenticated session by setting the session key 'login_auth_tk' to the `passwordhash`.

Note: If session IP validation is enabled, this API call must be executed via the local API to receive
a valid hash.

Note: The login functionality provided by this API is superseded by
CreateSsoToken (https://developers.whmcs.com/api-reference/createssotoken/) for remote login
functionality and OpenID Connect (https://go.whmcs.com/1993/openid-connect) for authentication
services/credential verification. This API may be deprecated in the future given these more robust
and modern implementations.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "ValidateLogin" | Required |
| email | string | User Email Address | Required |
| password2 | string | Password to validate | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| userid | int | User ID |
| passwordhash | string | Login session token - returned if Two-Factor Authentication is not required for the account |
| twoFactorEnabled | bool | True if Two-Factor Authentication is enabled for the given account |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'ValidateLogin',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'email' => 'user@example.com',
            'password2' => 'abc123',
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
$command = 'ValidateLogin';
$postData = array(
    'email' => 'user@example.com',
    'password2' => 'abc123',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "userid": "1",
    "passwordhash": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "twoFactorEnabled": "false"
}
```


### Error Responses

Possible error condition responses include:

* Email or Password Invalid


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
