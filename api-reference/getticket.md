+++
title = "GetTicket"
toc = true
+++

Obtain a specific ticket

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTicket" | Required |
| ticketnum | string | Obtain the ticket for the specific Client Ticket Number | Optional |
| ticketid | int | Obtain the ticket for the specific ticket id (Either $ticketnum or $ticketid is required) | Optional |
| repliessort | string | ASC or DESC. Which order to organise the ticket replies | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| ticketid | int | The unique Id of the ticket |
| tid | string | The unique ticket number string displayed to end users |
| c | string | The client unique access of the ticket |
| deptid | int | The id of the department the ticket belongs to |
| deptname | string | The name of the department the ticket belongs to |
| userid | int | The user id the ticket belongs to |
| contactid | int | The contact id the ticket was opened by |
| name | string | The name of the user |
| email | string | The email address of the user |
| cc | string | The cc email addresses for the ticket |
| date | \Carbon\Carbon | The date the ticket was opened Y-m-d H:i:s |
| subject | string | The subject of the ticket |
| status | string | The status of the ticket |
| priority | string | The priority of the ticket |
| admin | string | The name of the admin user who opened the ticket |
| lastreply | \Carbon\Carbon | The date the ticket was last replied to Y-m-d H:i:s |
| flag | int | The id of the admin user a ticket is flagged to |
| service | string | The id of the service associated with the ticket. Sx for services. Dx for domains |
| replies | array | an Array of replies on the ticket |
| notes | array | an Array of notes on the ticket |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTicket',
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
$command = 'GetTicket';
$postData = array(
    'ticketid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
null
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
