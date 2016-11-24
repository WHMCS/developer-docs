+++
title = "AddProjectTask"
toc = true
+++

Adds a Task to a project

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddProjectTask" | Required |
| projectid | int | The id of the project the task is for | Required |
| duedate | \Carbon\Carbon | The duedate for the task. Format YYYY-mm-dd | Required |
| adminid | int | The admin id to associate the task with | Optional |
| task | string | The task title | Optional |
| notes | string | The notes for the task | Optional |
| completed | bool | Has the task been completed | Optional |
| billed | bool | Has the task been billed | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| message | string | 'Task has been added' |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddProjectTask',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'projectid' => '1',
            'duedate' => '2016-01-01',
            'task' => 'This is a sample message',
            'adminid' => '2',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddProjectTask';
$postData = array(
    'projectid' => '1',
    'duedate' => '2016-01-01',
    'task' => 'This is a sample message',
    'adminid' => '2',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "message": "Task has been added"
}
```


### Error Responses

Possible error condition responses include:

* Project ID not Set
* Project ID Not Found
* Admin ID Not Found
* A task description must be specified


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
