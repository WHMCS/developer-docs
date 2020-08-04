+++
title = "UpdateProject"
toc = true
+++

Updates a project

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateProject" | Required |
| projectid | int | The project ID to update. | Required |
| adminid | int | The adminId the project will be associated with. | Optional |
| userid | int | The user that the project is for. | Optional |
| status | string | The status of the project as defined in Project Management Settings. | Optional |
| created | string | The created date of the project in the Y-m-d format. | Optional |
| duedate | string | The due date of the project in the Y-m-d format. | Optional |
| completed | bool | Whether the project is completed. | Optional |
| title | string | The title of the project. | Optional |
| ticketids | string | A comma-separated list of ticket IDs to associate with the project. | Optional |
| invoiceids | string | A comma-separated list of invoice IDs to associate with the project. | Optional |
| notes | string | The notes to associate with the project. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| message | string | 'Project Has Been Updated' |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateProject',
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
$command = 'UpdateProject';
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
    "message": "Project Has Been Updated"
}
```


### Error Responses

Possible error condition responses include:

* Project ID Not Set
* Project ID Not Found
* Client ID Not Found
* Admin ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
