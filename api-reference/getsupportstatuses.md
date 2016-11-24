+++
title = "GetSupportStatuses"
toc = true
+++

Get the support statuses and number of tickets in each status

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetSupportStatuses" | Required |
| deptid | int | Obtain counts for a specific department id | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| statuses | array | An array of status information |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetSupportStatuses',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetSupportStatuses';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": 6,
    "statuses": {
        "status": [
            {
                "title": "Open",
                "count": 1
            },
            {
                "title": "Answered",
                "count": 14
            },
            {
                "title": "Customer-Reply",
                "count": 3
            },
            {
                "title": "On Hold",
                "count": 0
            },
            {
                "title": "In Progress",
                "count": 0
            },
            {
                "title": "Closed",
                "count": 69
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
