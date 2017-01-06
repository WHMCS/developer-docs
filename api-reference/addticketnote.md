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
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'ticketid' => '1',
            'message' => 'This is a sample ticket note',
            'markdown' => 'true',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddTicketNote';
$postData = array(
    'ticketid' => '1',
    'message' => 'This is a sample ticket note',
    'markdown' => 'true',
);
$adminUsername = 'ADMIN_USERNAME';

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


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
