+++
title = "TriggerNotificationEvent"
toc = true
+++

Trigger a Custom Notification Event.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "TriggerNotificationEvent" | Required |
| notification_identifier | string | A unique identifier string, used as a condition when making a notification rule. | Optional |
| title | string | The title for the notification | Optional |
| message | string | The message body for the notification | Optional |
| url | string | The follow up URL for the notification | Optional |
| status | string | A status description for the notification | Optional |
| statusStyle | string | A formatting style for the status of the notification, currently supports "success", "danger", and "info" | Optional |
| attributes | array | An array of Attributes to include in the notification. Requires at least `label` and `value` parameters. Other parameters are optional. See WHMCS\Notification\NotificationAttribute. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'TriggerNotificationEvent',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'notification_identifier' => 'custom.server.add',
            'title' => 'New Server Added',
            'message' => 'new-server.examplehost.com added as a cPanel server and is available for provisioning.',
            'url' => 'https://whmcs.example.test/admin/configservers.php?action=manage&id=3',
            'status' => 'Success',
            'statusStyle' => 'info',
            'attributes[0][label]' => 'example',
            'attributes[0][value]' => 'example',
            'attributes[0][url]' => 'https://whmcs.example.test/admin/configservers.php?action=manage&id=3',
            'attributes[0][style]' => 'success',
            'attributes[0][icon]' => 'example',
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
$command = 'TriggerNotificationEvent';
$postData = array(
    'notification_identifier' => 'custom.server.add',
    'title' => 'New Server Added',
    'message' => 'new-server.examplehost.com added as a cPanel server and is available for provisioning.',
    'url' => 'https://whmcs.example.test/admin/configservers.php?action=manage&id=3',
    'status' => 'Success',
    'statusStyle' => 'info',
    'attributes[0][label]' => 'example',
    'attributes[0][value]' => 'example',
    'attributes[0][url]' => 'https://whmcs.example.test/admin/configservers.php?action=manage&id=3',
    'attributes[0][style]' => 'success',
    'attributes[0][icon]' => 'example',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success"
}
```


### Error Responses

Possible error condition responses include:

* API Notification Events require a identifier string to be passed.
* API Notification Events require a title to be provided.
* API Notification Events require a message to be provided.


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
