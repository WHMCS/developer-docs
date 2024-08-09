+++
title = "UpdateTicket"
toc = true
+++

Updates an existing ticket

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateTicket" | Required |
| ticketid | int | The ticket Id to update | Required |
| deptid | int | The department id of the ticket | Optional |
| status | string | The status of the ticket | Optional |
| subject | string | The subject of the ticket | Optional |
| userid | int | If applicable, the Client ID to update the ticket for. | Optional |
| name | string | The name of the person opening the ticket (if not a client) | Optional |
| email | string | The email address of the person opening the ticket (if not a client) | Optional |
| cc | string | The cc email addresses for the ticket | Optional |
| priority | string | The priority of the ticket ('Low', 'Medium', 'High') | Optional |
| created | string | The date and time the initial message will show as created. Format: ISO8601 or YYYY-MM-DD HH:mm:ss | Optional |
| flag | int | The id of the admin to flag the ticket to | Optional |
| removeFlag | bool | Remove the flag from the ticket | Optional |
| message | string | Update the ticket message | Optional |
| markdown | bool | Should markdown be used on the ticket output. | Optional |
| customfields | string | Base64 encoded serialized array of custom field values | Optional |
| preventClientClosure | bool | Whether the client should be allowed to close the ticket. If you do not pass this while also passing a department id, tickets moving to a department with the setting enabled will inherit the department setting. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| ticketid | int | The ticket id that has been updated |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateTicket',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'ticketid' => '1',
            'subject' => 'This is a sample updated ticket subject',
            'clientid' => '1',
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
$command = 'UpdateTicket';
$postData = array(
    'ticketid' => '1',
    'subject' => 'This is a sample updated ticket subject',
    'clientid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "ticketid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Ticket ID Not Found
* Department ID Not Found
* Invalid Ticket Priority. Valid priorities are: Low,Medium,High
* Invalid Ticket Status. Valid statuses are: xxx
* Invalid Date Format
* Ticket creation date cannot be in the future


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Added `message` parameter that allows updating primary ticket message. |
| 8.0 | Added support for ticket creation date. |
| 8.11 | Added optional `preventClientClosure` parameter to provide ability to allow client to close the ticket or not. |
