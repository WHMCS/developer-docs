+++
title = "UpdateTicketReply"
toc = true
+++

Updates a ticket reply message.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateTicketReply" | Required |
| replyid | int | The reply id to update. | Required |
| message | string | The message to be updated | Required |
| markdown | bool | Should markdown be used on the ticket message. Existing value is used if not supplied. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| replyid | int | The reply id that has been updated |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateTicketReply',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'replyid' => '1',
            'message' => 'This is a sample updated ticket reply',
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
$command = 'UpdateTicketReply';
$postData = array(
    'replyid' => '1',
    'message' => 'This is a sample updated ticket reply',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "replyid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Reply ID Required
* Message is Required
* Reply ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.7 | Initial Version |
