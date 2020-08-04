+++
title = "GetTicket"
toc = true
+++

Obtain a specific ticket

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTicket" | Required |
| ticketnum | string | A specific Client Ticket Number to find tickets for. | Optional |
| ticketid | int | A specific ticket ID to find tickets for (either $ticketnum or $ticketid is required). | Optional |
| repliessort | string | ASC or DESC. The order to use to organise the ticket replies. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| ticketid | int | The unique ID of the ticket. |
| tid | string | The unique ticket number string displayed to end users. |
| c | string | The client unique access of the ticket. |
| deptid | int | The ID of the department the ticket belongs to. |
| deptname | string | The name of the department the ticket belongs to. |
| userid | int | The user ID the ticket belongs to. |
| contactid | int | The contact ID the ticket was opened by. |
| name | string | The ticket submitter's name. |
| email | string | The ticket submitter's email. |
| requestor_name | string | The ticket submitter's name. |
| requestor_type | string | The ticket submitter's type. |
| requestor_email | string | The ticket submitter's email. |
| cc | string | The CC email addresses for the ticket. |
| date | string | The date the ticket was opened on. Format: Y-m-d H:i:s |
| subject | string | The subject of the ticket. |
| status | string | The status of the ticket. |
| priority | string | The priority of the ticket. |
| admin | string | The name of the admin user who opened the ticket. |
| lastreply | string | The date the ticket was last replied to. Format: Y-m-d H:i:s |
| flag | int | The ID of the admin user a ticket is flagged to. |
| service | string | The ID of the service associated with the ticket (Sx for services and Dx for domains). |
| replies | array | An array of replies on the ticket. |
| notes | array | An array of notes on the ticket. |


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
{
    "result": "success",
    "ticketid": "1",
    "tid": "516757",
    "c": "KPqH7yG3",
    "deptid": "1",
    "deptname": "Sample Support Department",
    "userid": "1",
    "contactid": "0",
    "name": "Cynthia Reilly",
    "email": "testuser@whmcs.com",
    "cc": "",
    "date": "2016-01-01 06:26:29",
    "subject": "This is a sample ticket",
    "status": "Closed",
    "priority": "Medium",
    "admin": "",
    "lastreply": "2016-01-01 06:30:16",
    "flag": "0",
    "service": "",
    "replies": {
        "reply": [
            {
                "replyid": "0",
                "userid": "1",
                "contactid": "0",
                "name": "Cynthia Reilly",
                "email": "testuser@whmcs.com",
                "requestor_name": "Cynthia Reilly",
                "requestor_email": "testuser@whmcs.com",
                "requestor_type": "Owner",
                "date": "2016-01-01 06:26:29",
                "message": "Hey, \r\n\r\nThis is the first ticket message!\r\n\r\nThanks\r\n\r\nCynthia",
                "attachment": "123456_attachment_name.png",
                "attachments": [
                    {
                        "filename": "attachment_name.png",
                        "index": 0
                    }
                ],
                "attachments_removed": true,
                "admin": ""
            },
            {
                "replyid": "1",
                "userid": "1",
                "contactid": "0",
                "name": "",
                "email": "",
                "requestor_name": "Demo Admin",
                "requestor_email": "",
                "requestor_type": "Operator",
                "date": "2016-01-01 06:27:01",
                "message": "Hello, \r\n\r\nThis is the first ticket reply by an admin user!\r\n\r\nThanks\r\n\r\nDemo Admin",
                "attachment": "",
                "attachments": [
                    []
                ],
                "attachments_removed": false,
                "admin": "Demo Admin",
                "rating": "0"
            },
            {
                "replyid": "2",
                "userid": "1",
                "contactid": "0",
                "name": "",
                "email": "",
                "requestor_name": "Cynthia Reilly",
                "requestor_email": "testuser@whmcs.com",
                "requestor_type": "Owner",
                "date": "2016-01-01 06:30:16",
                "message": "Hey, \r\n\r\nThis is a second reply!\r\n\r\nThanks\r\n\r\nCynthia",
                "attachment": "",
                "attachments": [
                    []
                ],
                "attachments_removed": false,
                "admin": "",
                "rating": "0"
            }
        ]
    },
    "notes": {
        "note": [
            {
                "noteid": "1",
                "date": "2016-01-01 06:26:42",
                "message": "This is a ticket note",
                "attachment": "",
                "attachments": [
                    []
                ],
                "attachments_removed": false,
                "admin": "Demo Admin"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.10 | Added new return parameter `attachments`. |
| 8.0 | Added new return parameters `requestor_name`, `requestor_type`, and `requestor_email`. |
