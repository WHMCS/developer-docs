+++
title = "AddClientNote"
toc = true
+++

Adds a Client Note

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddClientNote" | Required |
| userid | int | The Client ID to apply the note to | Required |
| notes | string | The note to add | Required |
| sticky | bool | Should the note be made sticky. Makes the note 'sticky' and displays the note throughout the client's account and on any tickets they submit in the admin area | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| noteid | int | The id of the newly created note |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddClientNote',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'userid' => '1',
            'notes' => 'Note to add',
            'sticky' => true,
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
$command = 'AddClientNote';
$postData = array(
    'userid' => '1',
    'notes' => 'Note to add',
    'sticky' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "noteid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Client ID not found
* Notes can not be empty


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
