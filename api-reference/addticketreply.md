+++
title = "AddTicketReply"
toc = true
+++

Add a reply to a ticket by Ticket ID.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddTicketReply" | Required |
| ticketid | int | The id of the ticket in the database. $ticketid is required | Required |
| message | string | The content of the ticket reply | Required |
| markdown | bool | Should markdown be used on the ticket reply output | Optional |
| clientid | int | Pass a clientid to associate the ticket reply with a specific client | Optional |
| contactid | int | Pass a contactid to associate the ticket reply with a specific contact belonging to $clientid | Optional |
| adminusername | string | The admin username to associate the ticket reply with | Optional |
| name | string | The name to associate with the ticket reply if not an admin or client response | Optional |
| email | string | The email to associate with the ticket reply if not an admin or client response | Optional |
| status | string | The status to set on the ticket after the reply is made if the default status on admin/client response is not required. See GetSupportStatuses API command | Optional |
| noemail | bool | Set to true to stop the ticket reply email being sent | Optional |
| customfields | string | A base64 encoded array of the custom fields to update | Optional |
| attachments | array | Optional base64 json encoded array of file attachments. Can be the direct output of a multipart-form-data form submission ($_FILES superglobal in PHP) or an array of arrays consisting of both a filename and data keys (see example below). | Optional |
| created | string | The date and time the ticket reply will show as sent. Format: ISO8601 or YYYY-MM-DD HH:mm:ss | Optional |

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
            'action' => 'AddTicketReply',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'ticketid' => '1',
            'message' => 'This is a sample ticket reply',
            'clientid' => '1',
            'customfields' => base64_encode(serialize(array("1"=>"Google"))),
            'markdown' => true,
            'attachments' => base64_encode(json_encode([['name' => 'sample_text_file.txt', 'data' => base64_encode('This is a sample text file contents')]])),
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
$command = 'AddTicketReply';
$postData = array(
    'ticketid' => '1',
    'message' => 'This is a sample ticket reply',
    'clientid' => '1',
    'customfields' => base64_encode(serialize(array("1"=>"Google"))),
    'markdown' => true,
    'attachments' => base64_encode(json_encode([['name' => 'sample_text_file.txt', 'data' => base64_encode('This is a sample text file contents')]])),
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

* Ticket ID not found
* Client ID Not Found
* Contact ID Not Found
* Name and email address are required if not a client
* Message is required
* Email Address Invalid
* Invalid Ticket Status
* Invalid Date Format
* Reply creation date cannot be in the future


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.5 | Added support for attachments |
| 8.0 | Added support for ticket reply date and time |
