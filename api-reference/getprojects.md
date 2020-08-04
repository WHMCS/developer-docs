+++
title = "GetProjects"
toc = true
+++

Obtain orders matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetProjects" | Required |
| limitstart | int | The offset for the returned project data (default: `0`). | Optional |
| limitnum | int | The number of records to return (default: `25`). | Optional |
| userid | int | A specific client ID to find projects for. | Optional |
| title | string | A specific title to find projects for. | Optional |
| ticketids | string | Specific ticket IDs to find projects for. | Optional |
| invoiceids | string | Specific invoice IDs to find projects for. | Optional |
| notes | string | Specific notes to find projects for. | Optional |
| adminid | int | A specific admin ID to find projects for. | Optional |
| status | string | A specific status to find projects for. | Optional |
| created | string | A specific creation date to find projects for. | Optional |
| duedate | string | A specific due date to find projects for. | Optional |
| completed | bool | Whether to find projects that are or aren't completed. | Optional |
| lastmodified | string | A specific last modified date to find projects for. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available. |
| startnumber | int | The starting number for the returned results. |
| numreturned | int | The number of results returned. |
| invoices | array | An array of invoices matching the passed criteria. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetProjects',
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
$command = 'GetProjects';
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
    "totalresults": 1,
    "startnumber": 0,
    "numreturned": 1,
    "projects": [
        {
            "id": 1,
            "userid": 0,
            "title": "First Project",
            "ticketids": "",
            "invoiceids": "",
            "notes": "",
            "adminid": 1,
            "status": "Pending",
            "created": "2020-06-24",
            "duedate": "2020-06-24",
            "completed": 0,
            "lastmodified": "2020-06-24 10:26:23",
            "watchers": ""
        }
    ]
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
