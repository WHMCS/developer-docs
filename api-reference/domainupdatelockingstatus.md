+++
title = "DomainUpdateLockingStatus"
toc = true
+++

Sends the Update Lock command to the registrar for the domain

Connects to the registrar and attempts to update the lock

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DomainUpdateLockingStatus" | Required |
| domainid | int | The id of the domain to update the locking status for | Required |
| lockstatus | bool | Should the domain lock be turned on | Optional |

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
            'action' => 'DomainUpdateLockingStatus',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'domainid' => '1',
            'lockstatus' => true,
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
$command = 'DomainUpdateLockingStatus';
$postData = array(
    'domainid' => '1',
    'lockstatus' => true,
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
* An invalid configuration was detected with the registrar module


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
