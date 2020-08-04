+++
title = "UpdateProjectTask"
toc = true
+++

Adds a Task to a project

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateProjectTask" | Required |
| taskid | int | The ID of the project task to update. | Required |
| projectid | int | Change the project a task is assigned to. | Optional |
| duedate | string | The due date for the task. Format: YYYY-mm-dd | Optional |
| adminid | int | The admin ID to associate the task with. | Optional |
| task | string | The task title. | Optional |
| notes | string | The notes for the task. | Optional |
| completed | bool | Whether this task has been completed. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| message | string | 'Task has been updated' |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateProjectTask',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'projectid' => '1',
            'duedate' => '2016-01-01',
            'task' => 'This is a sample message',
            'adminid' => '2',
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
$command = 'UpdateProjectTask';
$postData = array(
    'projectid' => '1',
    'duedate' => '2016-01-01',
    'task' => 'This is a sample message',
    'adminid' => '2',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

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

* Task ID is Required
* Project ID Not Found
* Task ID Not Found
* Admin ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
