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
| userid | int | The ID of the user to obtain the log for | Optional |
| date | string | The date of the activity log to retrieve in localised format (eg 01/01/2016) | Optional |
| user | string | The name of the user to retrieve the log entries for | Optional |
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
    "totalresults": "2",
    "startnumber": "0",
    "activity[entry][0][id]": "2",
    "activity[entry][0][userid]": "0",
    "activity[entry][0][date]": "2016-01-01 17:24:26",
    "activity[entry][0][description]": "Cron Job: Check for Updates: No new updates available",
    "activity[entry][0][username]": "admin",
    "activity[entry][0][ipaddress]": "192.168.99.1",
    "activity[entry][1][id]": "1",
    "activity[entry][1][userid]": "0",
    "activity[entry][2][date]": "2016-01-01 17:24:20",
    "activity[entry][1][description]": "Cron Job: Perform WHMCS Update Check",
    "activity[entry][1][username]": "admin",
    "activity[entry][1][ipaddress]": "192.168.99.1"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
