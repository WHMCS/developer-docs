+++
title = "MergeTicket"
toc = true
+++

Merge tickets.

Merges multiple tickets into a single ticket. This cannot be undone.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "MergeTicket" | Required |
| ticketid | int | The unique ticket id that `mergeticketids` will be merged into | Required |
| mergeticketids | string | A comma separated list of ticket ids to merge into `ticketid` | Required |
| newsubject | string | An optional subject to be set on the `ticketid` | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| ticketid | int |  |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'MergeTicket',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'ticketid' => '1',
            'mergeticketids' => '2,3,4,5,6,7',
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
$command = 'MergeTicket';
$postData = array(
    'ticketid' => '1',
    'mergeticketids' => '2,3,4,5,6,7',
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

* Ticket ID Required
* Ticket ID Invalid
* Merge Ticket IDs Required
* Invalid Merge Ticket IDs: x, x...,


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.10.0 | Initial Version |
