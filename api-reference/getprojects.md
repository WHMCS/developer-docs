+++
title = "GetProjects"
toc = true
+++

Obtain orders matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetProjects" | Required |
| limitstart | int | The offset for the returned project data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| userid | int | Find projects for a specific client id | Optional |
| title | string | Find projects with a specific title | Optional |
| ticketids | string | Find projects with specific ticketids | Optional |
| invoiceids | string | Find projects with specific invoiceids | Optional |
| notes | string | Find projects with specific notes | Optional |
| adminid | int | Find projects assigned to a specific admin id | Optional |
| status | string | Find projects with a specific status | Optional |
| created | \Carbon\Carbon | Find projects with a specific creation date | Optional |
| duedate | \Carbon\Carbon | Find projects with a specific due date | Optional |
| completed | bool | Find projects that are/aren't completed | Optional |
| lastmodified | \Carbon\Carbon | Find projects with a specific last modified date | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| invoices | array | An array of invoices matching the criteria passed |


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
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "projects[0][id]": "1",
    "projects[0][userid]": "1",
    "projects[0][title]": "Test Project",
    "projects[0][attachments]": "",
    "projects[0][ticketids]": "",
    "projects[0][invoiceids]": "",
    "projects[0][notes]": "",
    "projects[0][adminid]": "1",
    "projects[0][status]": "Pending",
    "projects[0][created]": "2016-01-01",
    "projects[0][duedate]": "2016-01-09",
    "projects[0][completed]": "0",
    "projects[0][lastmodified]": "2016-1-02 13:59:01"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
