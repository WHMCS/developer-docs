+++
title = "GetActivityLog"
toc = true
+++

Obtain the Activity Log that matches passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetActivityLog" | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| clientid | int | The ID of the client to obtain the log for. | Optional |
| date | string | The date of the activity log to retrieve in localised format (eg 01/01/2016) | Optional |
| user | string | The client email, user email, or admin username to retrieve the log entries for. | Optional |
| description | string | Search the log for a specific string | Optional |
| ipaddress | string | The IP Address to search the activity log for | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| activity | array | The activity log entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetActivityLog',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'description' => 'Cron Job',
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
$command = 'GetActivityLog';
$postData = array(
    'description' => 'Cron Job',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": 2,
    "startnumber": 0,
    "activity": {
        "entry": [
            {
                "id": 2,
                "clientId": 0,
                "userId": 0,
                "adminId": 1,
                "date": "2021-01-01 06:56:49",
                "description": "Cron Job: Check for Updates: No new updates available",
                "username": "admin",
                "ipaddress": "172.18.0.1",
                "userid": 0
            },
            {
                "id": 1,
                "clientId": 0,
                "userId": 0,
                "adminId": 1,
                "date": "2021-01-01 06:56:49",
                "description": "Cron Job: Perform WHMCS Update Check",
                "username": "admin",
                "ipaddress": "172.18.0.1",
                "userid": 0
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.0 | Added `userId` to response. Renamed `userid` response to `clientId`. `userid` may be removed in a future version. |
| 8.5 | Renamed `userid` parameter to `clientid`. Backwards compatibility preserved for `userid`. |
