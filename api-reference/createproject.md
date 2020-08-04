+++
title = "CreateProject"
toc = true
+++

Creates a new project

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateProject" | Required |
| title | string | The title of the new project. | Required |
| adminid | int | The admin ID the project will be associated with. | Required |
| userid | int | The user who the project is for. | Optional |
| status | string | The status of the project, as defined in Project Management Settings. | Optional |
| created | string | The created date of the project in `Y-m-d` format. | Optional |
| duedate | string | The due date date of the project in `Y-m-d` format. | Optional |
| completed | bool | Whether the project is complete. | Optional |
| ticketids | string | A comma-separated list of ticket IDs to associate with the project. | Optional |
| invoiceids | string | A comma-separated list of invoice IDs to associate with the project. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| message | string | 'Project has been created' |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'CreateProject',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'title' => 'This is a Test Project',
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
$command = 'CreateProject';
$postData = array(
    'title' => 'This is a Test Project',
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
    "message": "Project has been created",
    "projectid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* Admin ID not Set
* Admin ID Not Found
* Project Management is not active.
* Project Title is Required.


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
