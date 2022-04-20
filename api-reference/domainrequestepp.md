+++
title = "DomainRequestEPP"
toc = true
+++

Sends the Request EPP command to the registrar for the domain

Connects to the registrar and attempts to obtain the EPP Code for the domain.
Not all registrars return the EPP code but send them directly to the client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DomainRequestEPP" | Required |
| domainid | int | The id of the domain to obtain the EPP for | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| eppcode | string | If supported, the EPP code. No returned EPP code without error suggests it is sent directly to client. A returned EPP code may include HTML character entities intended for display and should be decoded prior to any direct use. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'DomainRequestEPP',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'domainid' => '1',
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
$command = 'DomainRequestEPP';
$postData = array(
    'domainid' => '1',
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

* Domain ID Not Found
* Registrar Error Message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
