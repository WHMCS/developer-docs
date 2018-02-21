+++
title = "GetCancelledPackages"
toc = true
+++

Obtain an array of cancellation requests

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetCancelledPackages" | Required |
| limitstart | int | The offset for the returned cancellation request data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| packages | array | The cancellation request entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetCancelledPackages',
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
$command = 'GetCancelledPackages';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "2",
    "startnumber": "0",
    "numreturned": "2",
    "packages[package][0][id]": "1",
    "packages[package][0][date]": "2016-02-24 21:27:04",
    "packages[package][0][relid]": "1",
    "packages[package][0][reason]": "Client Requested",
    "packages[package][0][type]": "End of Billing Period",
    "packages[package][0][created_at]": "0000-00-00 00:00:00",
    "packages[package][0][updated_at]": "0000-00-00 00:00:00",
    "packages[package][1][id]": "2",
    "packages[package][1][date]": "2016-02-24 21:27:04",
    "packages[package][1][relid]": "2",
    "packages[package][1][reason]": "Client Requested",
    "packages[package][1][type]": "Immediate",
    "packages[package][1][created_at]": "0000-00-00 00:00:00",
    "packages[package][1][updated_at]": "0000-00-00 00:00:00"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
