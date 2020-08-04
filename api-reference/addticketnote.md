+++
title = "AddTicketNote"
toc = true
+++

Add a note to a ticket by Ticket ID or Ticket Number.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddTicketNote" | Required |
| message | string | The content of the ticket note | Required |
| ticketnum | string | The Client Ticket Number ID to apply the note to | Optional |
| ticketid | int | The id of the ticket in the database. Either $ticketnum or $ticketid is required | Optional |
| markdown | bool | Should markdown be used on the ticket note output | Optional |
| attachments | array | Optional base64 json encoded array of file attachments. Can be the direct output of a multipart-form-data form submission ($_FILES superglobal in PHP) or an array of arrays consisting of both a filename and data keys (see example below). | Optional |
| created | string | The date and time the ticket note will show as created. Format: ISO8601 or YYYY-MM-DD HH:mm:ss | Optional |

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
            'action' => 'AddTicketNote',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'ticketid' => '1',
            'message' => 'This is a sample ticket note',
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
$command = 'AddTicketNote';
$postData = array(
    'ticketid' => '1',
    'message' => 'This is a sample ticket note',
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
* Message is required
* Invalid Date Format
* Ticket creation date cannot be in the future


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.5 | Added support for attachments |
| 8.0 | Add support for note creation date |
