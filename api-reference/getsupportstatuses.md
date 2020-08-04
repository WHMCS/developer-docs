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
$command = 'GetSupportStatuses';
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
    "totalresults": 6,
    "statuses": {
        "status": [
            {
                "title": "Open",
                "count": 12,
                "color": "#779500"
            },
            {
                "title": "Answered",
                "count": 43,
                "color": "#000000"
            },
            {
                "title": "Customer-Reply",
                "count": 6,
                "color": "#ff6600"
            },
            {
                "title": "On Hold",
                "count": 0,
                "color": "#224488"
            },
            {
                "title": "In Progress",
                "count": 3,
                "color": "#cc0000"
            },
            {
                "title": "Closed",
                "count": 3562,
                "color": "#888888"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.0 | Provide defined status color for a respective status within `$statuses` array. |
