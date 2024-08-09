+++
title = "OpenTicket"
toc = true
+++

Open a new ticket

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "OpenTicket" | Required |
| deptid | int | The department to open the ticket in | Required |
| subject | string | The subject of the ticket | Required |
| message | string | The message of the ticket | Required |
| clientid | int | If applicable, the Client ID to create the ticket for. | Optional |
| userid | int | If applicable, the user ID to create the ticket for (if $clientid is also passed). | Optional |
| contactid | int | If applicable, the Contact ID to create the ticket for (if $clientid and no $userid is also passed). | Optional |
| name | string | The name of the person opening the ticket (if not a client) | Optional |
| email | string | The email address of the person opening the ticket (if not a client) | Optional |
| priority | string | The priority of the ticket ('Low', 'Medium', 'High') | Optional |
| created | string | The date and time the ticket message will show as sent. Format: ISO8601 or YYYY-MM-DD HH:mm:ss | Optional |
| serviceid | int | The service to associate the ticket with (only one of $serviceid or $domainid) | Optional |
| domainid | int | The domain to associate the ticket with (only one of $serviceid or $domainid) | Optional |
| admin | bool | Whether the ticket opener is an Admin. If you pass this, you must also pass the admin's username with localAPI call arguments. Otherwise, the system still uses the client as the ticket opener. | Optional |
| noemail | bool | Pass 'true' for this value to prevent the ticket email from being sent. | Optional |
| markdown | bool | Should markdown be used on the ticket output | Optional |
| customfields | string | Base64 encoded serialized array of custom field values | Optional |
| attachments | array | Optional base64 json encoded array of file attachments. Can be the direct output of a multipart-form-data form submission ($_FILES superglobal in PHP) or an array of arrays consisting of both a filename and data keys (see example below). | Optional |
| preventClientClosure | bool | Whether the client should be allowed to close the ticket. If you do not pass this, the ticket will inherit the department setting. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| id | int | The unique id of the newly created ticket |
| tid | string | The unique ticket id displayed to the client, and to load the ticket in the client area |
| c | string | The code to access the ticket in the client area |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'OpenTicket',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'deptid' => '1',
            'subject' => 'This is a sample ticket',
            'message' => 'This is a **sample** ticket message',
            'clientid' => '1',
            'priority' => 'Medium',
            'markdown' => true,
            'attachments' => base64_encode(json_encode([['name' => 'sample_text_file.txt', 'data' => base64_encode('This is a sample text file contents')]])),
            'preventClientClosure' => true,
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
$command = 'OpenTicket';
$postData = array(
    'deptid' => '1',
    'subject' => 'This is a sample ticket',
    'message' => 'This is a **sample** ticket message',
    'clientid' => '1',
    'priority' => 'Medium',
    'markdown' => true,
    'attachments' => base64_encode(json_encode([['name' => 'sample_text_file.txt', 'data' => base64_encode('This is a sample text file contents')]])),
    'preventClientClosure' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "id": "1",
    "tid": "516757",
    "c": "KPqH7yG3"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* The system cannot find the provided user ID.
* Contact ID Not Found
* Name and email address are required if not a client
* Department ID not found
* Subject is required
* Message is required
* Service ID Not Found
* Domain ID Not Found
* Email Address Invalid
* Invalid Date Format
* Ticket creation date cannot be in the future
* Unable to generate ticket number


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.11 | Added optional `preventClientClosure` parameter to provide ability to define whether the client should be allowed to close the ticket. |
| 7.5 | Added support for attachments. |
| 8.0 | Added support for ticket creation date. |
| 8.3 | Added support for stopping email from being sent. |
| 8.3 | Added error message if a ticket number is unable to be generated. |
| 8.5 | Added support for the $userid parameter. |
