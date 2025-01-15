+++
title = "GetAutomationLog"
toc = true
+++

Get Automation Task Log.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetAutomationLog" | Required |
| startdate | string | Defaults to today | Optional |
| enddate | string | Defaults to today | Optional |
| namespace | string | Optional filter for a specific namespace | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| currentDatetime | string | The current system datetime. |
| lastDailyCronInvocationTime | string | The last daily cron invocation time. |
| startdate | string | The start date/time filter applied |
| enddate | string | The end date/time filter applied |
| statistics | array | The log output, grouped by date and namespace |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetAutomationLog',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'startdate' => '2016-11-01',
            'enddate' => '2016-11-07',
            'namespace' => 'createinvoices',
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
$command = 'GetAutomationLog';
$postData = array(
    'startdate' => '2016-11-01',
    'enddate' => '2016-11-07',
    'namespace' => 'createinvoices',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "currentDatetime": "2016-11-09 15:37:58",
    "lastDailyCronInvocationTime": "2016-11-09 11:00:00",
    "startdate": "2016-11-01 00:00:00",
    "enddate": "2016-11-07 23:59:59",
    "statistics": "...."
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
