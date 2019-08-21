+++
title = "UpdateOAuthCredential"
toc = true
+++

Updates a given OAuth API Client Credential.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateOAuthCredential" | Required |
| credentialId | int | The auto increment ID of the credential set to be updated | Required |
| clientApiIdentifier | string | The OAuth API Client Credential Unique Identifier (Client ID) to be updated. Only required if credentialId is not known/passed. | Optional |
| name | string | The name to assign | Optional |
| description | string | The description to assign | Optional |
| grantType | string | The grant type for which the credential set is valid for. Possible values include: *authorization_code* or *single_sign_on* | Optional |
| scope | string | A space delimited list of the scopes for which the credential set is valid. See **CreateOAuthCredential** for permitted values | Optional |
| serviceId | int | The service ID for which the credential relates to | Optional |
| logoUri | string[] | he logoUri to assign | Optional |
| redirectUri | string | An array of Authorized Redirect URIs | Optional |
| resetSecret | bool | Set to true to reset the OAuth API Client Credential Secret | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| credentialId | int | The auto increment ID for the credential set |
| newClientSecret | string | Present only if resetSecret is passed as true |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateOAuthCredential',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'credentialId' => '1',
            'name' => 'Credential name',
            'resetSecret' => true,
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
$command = 'UpdateOAuthCredential';
$postData = array(
    'credentialId' => '1',
    'name' => 'Credential name',
    'resetSecret' => true,
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
    "newClientSecret": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```


### Error Responses

Possible error condition responses include:

* A Credential ID or Client Identifier is required.
* Invalid Credential ID provided.
* Invalid Client Identifier provided.
* The requested grant type "xxxxx" is invalid.
* A name for the Client Credential is required.
* A service ID is required for the single sign-on grant type.
* The requested scope "xxxxxxx" is invalid.


### Version History

| Version | Changelog |
| ------- | --------- |
| 6.2.0 | Initial Version |
