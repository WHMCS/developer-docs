+++
title = "UpdateAnnouncement"
toc = true
+++

Update a specific announcement

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateAnnouncement" | Required |
| announcementid | string | The ID of the announcement to update. | Required |
| title | string | The title of the announcement (if required to change). | Optional |
| announcement | string | The message of the announcement (if required to change). | Optional |
| date | string | The date of the announcement (if required to change). Format: Y-m-d H:i:s | Optional |
| published | bool | Whether to publish the announcement (1 or 0) (if required to change). | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| announcementid | int | The ID of the updated announcement. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateAnnouncement',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'notes' => 'This is an admin note',
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
$command = 'UpdateAnnouncement';
$postData = array(
    'notes' => 'This is an admin note',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "announcementid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Announcement ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
