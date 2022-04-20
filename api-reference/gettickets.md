+++
title = "GetTickets"
toc = true
+++

Obtain tickets matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTickets" | Required |
| limitstart | int | The offset for the returned quote data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| deptid | int | Obtain tickets in a specific department | Optional |
| clientid | int | Find tickets for a specific client id | Optional |
| email | string | Find tickets for a specific non-client email address | Optional |
| status | string | Find tickets matching a specific status. Any configured status plus: `Awaiting Reply`, `All Active Tickets`, `My Flagged Tickets` | Optional |
| subject | string | Find tickets containing a specific subject - uses approximate string matching. | Optional |
| ignore_dept_assignments | bool | Pass as true to not adhere to the departments the API user is a member of. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| tickets | array | An array of tickets matching the criteria passed |
| requestor_name | string | The ticket submitter's name. |
| requestor_type | string | The ticket submitter's type. |
| requestor_email | string | The ticket submitter's email. |
| owner_name | string | The ticket submitter's owner. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTickets',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
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
$command = 'GetTickets';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "1",
    "startnumber": 0,
    "numreturned": 1,
    "tickets": {
        "ticket": [
            {
                "id": "1",
                "tid": "516757",
                "deptid": "1",
                "userid": "1",
                "name": "Cynthia Reilly",
                "owner_name": "Cynthia Reilly",
                "email": "testuser@whmcs.com",
                "requestor_name": "Cynthia Reilly",
                "requestor_email": "testuser@whmcs.com",
                "requestor_type": "Owner",
                "cc": "",
                "c": "KPqH7yG3",
                "date": "2016-01-01 06:26:29",
                "subject": "This is a sample ticket",
                "status": "Answered",
                "priority": "Medium",
                "admin": "admin admin",
                "attachment": "123456_attachment_name.png",
                "attachments": [
                    {
                        "filename": "attachment_name.png",
                        "index": 0
                    }
                ],
                "attachments_removed": true,
                "lastreply": "2016-01-01 06:30:16",
                "flag": "0",
                "service": ""
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.10 | Added new return parameter `attachments` |
| 8.0 | Added new return parameters `requestor_name`, `requestor_type`, `requestor_email`, and `owner_name`. |
