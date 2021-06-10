+++
title = "BlockTicketSender"
toc = true
+++

Blocks a ticket sender.

Blocks an unregistered ticket sender, optionally deleting the ticket. Deleting the ticket cannot be undone.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "BlockTicketSender" | Required |
| ticketid | int | The ticket the sender opened | Required |
| delete | bool | Should the ticket also be deleted | Optional |

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
            'action' => 'BlockTicketSender',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'ticketid' => '1',
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
$command = 'BlockTicketSender';
$postData = array(
    'ticketid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "deleted": "true"
}
```


### Error Responses

Possible error condition responses include:

* Ticket ID Required
* Ticket ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.10.0 | Initial Version |
