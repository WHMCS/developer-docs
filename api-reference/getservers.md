+++
title = "GetServers"
toc = true
+++

Get servers.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetServers" | Required |
| serviceId | int | Pass a Product/Service ID to fetch available servers for its module type. | Optional |
| addonId | int | Pass a Addon/Service ID to fetch available servers for its module type. | Optional |
| fetchStatus | bool | Pass as true to attempt to fetch server status values. | Optional |

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
            'action' => 'GetServers',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'serviceId' => '1',
            'fetchStatus' => false,
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
$command = 'GetServers';
$postData = array(
    'serviceId' => '1',
    'fetchStatus' => false,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "servers": [
        {
            "id": 1,
            "name": "Sample cPanel Box",
            "hostname": "hostname.example.com",
            "ipaddress": "10.100.4.30",
            "active": true,
            "activeServices": 0,
            "maxAllowedServices": 200,
            "percentUsed": 0,
            "module": "cpanel",
            "status": {
                "http": false,
                "load": "",
                "uptime": ""
            }
        }
    ],
    "fetchStatus": ""
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
