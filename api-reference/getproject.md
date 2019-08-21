+++
title = "GetProject"
toc = true
+++

Retrieve a specific Project

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetProject" | Required |
| projectid | int | The project id to obtain | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| projectinfo | array | The project data |
| tasks | array | The project tasks and data |
| messages | array | The project messages and data |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetProject',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'projectid' => '1',
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
$command = 'GetProject';
$postData = array(
    'projectid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "projectinfo[id]": "1",
    "projectinfo[userid]": "1",
    "projectinfo[title]": "Test Project",
    "projectinfo[attachments] ": ">",
    "projectinfo[ticketids] ": ">",
    "projectinfo[invoiceids] ": ">",
    "projectinfo[notes] ": ">",
    "projectinfo[adminid]": "1",
    "projectinfo[status]": "Pending",
    "projectinfo[created]": "2016-01-01",
    "projectinfo[duedate]": "2016-01-09",
    "projectinfo[completed]": "0",
    "projectinfo[lastmodified]": "2016-1-02 13:59:01",
    "tasks[task][0][id]": "1",
    "tasks[task][0][projectid]": "1",
    "tasks[task][0][task]": "Task 1",
    "tasks[task][0][notes] ": ">",
    "tasks[task][0][adminid]": "0",
    "tasks[task][0][created]": "2016-01-02 11:57:57",
    "tasks[task][0][duedate]": "0000-00-00",
    "tasks[task][0][completed]": "0",
    "tasks[task][0][billed]": "0",
    "tasks[task][0][order]": "1",
    "tasks[task][0][timelogs][timelog][0][id]": "1",
    "tasks[task][0][timelogs][timelog][0][projectid]": "1",
    "tasks[task][0][timelogs][timelog][0][taskid]": "1",
    "tasks[task][0][timelogs][timelog][0][adminid]": "1",
    "tasks[task][0][timelogs][timelog][0][start]": "1451739482",
    "tasks[task][0][timelogs][timelog][0][end]": "1451743110",
    "tasks[task][0][timelogs][timelog][0][donotbill]": "0",
    "tasks[task][0][timelogs][timelog][0][starttime]": "2016-01-02 12:58:02",
    "tasks[task][0][timelogs][timelog][0][endtime]": "2016-01-02 13:58:30",
    "tasks[task][1][id]": "2",
    "tasks[task][1][projectid]": "1",
    "tasks[task][1][task]": "Task 2",
    "tasks[task][1][notes] ": ">",
    "tasks[task][1][adminid]": "0",
    "tasks[task][1][created]": "2016-01-02 13:58:01",
    "tasks[task][1][duedate]": "0000-00-00",
    "tasks[task][1][completed]": "0",
    "tasks[task][1][billed]": "0",
    "tasks[task][1][order]": "2",
    "tasks[task][1][timelogs]": "",
    "messages[message][0][id]": "1",
    "messages[message][0][projectid]": "1",
    "messages[message][0][date]": "2016-10-04 13:59:01",
    "messages[message][0][message]": "Message 1",
    "messages[message][0][attachments] ": ">",
    "messages[message][0][adminid]": "1"
}
```


### Error Responses

Possible error condition responses include:

* Project ID Not Set
* Project ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
