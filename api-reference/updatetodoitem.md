+++
title = "UpdateToDoItem"
toc = true
+++

Update To-Do Item.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateToDoItem" | Required |
| itemid | int | The To-Do item's ID. | Required |
| adminid | int | The ID of the admin user updating the To-Do item. | Required |
| status | string | The status of the To-Do item. | Optional |
| date | int | The date for the To-Do item. | Optional |
| title | string | The To-Do item's title. | Optional |
| description | string | A description of the To-Do item. | Optional |
| duedate | int | The To-Do item's due date. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| itemid | int | The ID of the affected To-Do item. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateToDoItem',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'itemid' => '1',
            'adminid' => '1',
            'status' => 'Completed',
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
$command = 'UpdateToDoItem';
$postData = array(
    'itemid' => '1',
    'adminid' => '1',
    'status' => 'Completed',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "itemid": "1"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
