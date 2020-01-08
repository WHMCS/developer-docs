+++
title = "CreateOAuthCredential"
toc = true
+++

Create an OAuth Credential

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateOAuthCredential" | Required |
| grantType | string | One of 'authorization_code' or 'single_sign_on' | Required |
| scope | string | A space separated list of valid scopes from tbloauthserver_scopes | Required |
| name | string | The name to give the oAuth Credential for the authorization_code $grantType | Optional |
| serviceId | int | The id of the service for the single_sign_on $grantType | Optional |
| description | string | The description of the OAuth Credential | Optional |
| logoUri | string | URL or Path Relative to the Base WHMCS Client Area Directory to a logo image file for this application. | Optional |
| redirectUri | string | Authorised Redirect URIs | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| credentialId | int | The ID of the newly created oauth credential |
| clientIdentifier | string | The randomly generated oauth client identifier |
| clientSecret | string | The randomly generated secret for the auth credential |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'CreateOAuthCredential',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'grantType' => 'single_sign_on',
            'scope' => 'clientarea:sso clientarea:billing_info clientarea:announcements',
            'serviceId' => '1',
            'description' => 'Billing and Announcements SSO',
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
$command = 'CreateOAuthCredential';
$postData = array(
    'grantType' => 'single_sign_on',
    'scope' => 'clientarea:sso clientarea:billing_info clientarea:announcements',
    'serviceId' => '1',
    'description' => 'Billing and Announcements SSO',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "credentialId": "1",
    "clientIdentifier": "COMPANY-NAME.SQxOYrZOUTQC8YTkLQuQ0w==",
    "clientSecret": "60XScB\/W8zzxtciWlvX8+OoO4ZAQj8dNLeFIulRlYhDgksrSJd0Olv+X7wyoJEWEOpZ9IivCaySN7s+\/a++Tlg=="
}
```


### Error Responses

Possible error condition responses include:

* A valid grant type is required.
* The requested grant type "x" is invalid.
* A name for the Client Credential is required.
* A service ID is required for the single sign-on grant type.
* At least one valid scope is required.
* The requested scope "x" is invalid.
* A valid Service ID is required.
* Service ID not associated with valid Client.


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
