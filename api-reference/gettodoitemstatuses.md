+++
title = "GetToDoItemStatuses"
toc = true
+++

Obtain To Do item statuses and counts

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetToDoItemStatuses" | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| todoitemstatuses | array | An array of to do item statuses and counts |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetToDoItemStatuses',
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
$command = 'GetToDoItemStatuses';
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
    "totalresults": 5,
    "todoitemstatuses": {
        "status": [
            {
                "type": "New",
                "count": 1,
                "overdue": 0
            },
            {
                "type": "Pending",
                "count": 4,
                "overdue": 2
            },
            {
                "type": "In Progress",
                "count": 10,
                "overdue": 10
            },
            {
                "type": "Completed",
                "count": 20,
                "overdue": 0
            },
            {
                "type": "Postponed",
                "count": 10,
                "overdue": 0
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
