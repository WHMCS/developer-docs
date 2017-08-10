+++
title = "GetEmails"
toc = true
+++

Obtain a list of emails sent to a specific Client ID

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetEmails" | Required |
| clientid | int | The Client ID to retrieve the emails for | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| date | \Carbon\Carbon | The date to retrieve emails for. | Optional |
| subject | string | The subject to retrieve emails for - uses approximate string matching. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The total number of results returned |
| emails | array | The activity log entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetEmails',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'subject' => 'elcom',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetEmails';
$postData = array(
    'clientid' => '1',
    'subject' => 'elcom',
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
    "startnumber": "0",
    "numreturned": "1",
    "emails[email][0][id]": "1",
    "emails[email][0][userid]": "1",
    "emails[email][0][subject]": "Welcome",
    "emails[email][0][message]": "*html email content*",
    "emails[email][0][date]": "2016-01-01 13:26:50",
    "emails[email][0][to]": "Test Client <test@example.com>",
    "emails[email][0][cc]": "",
    "emails[email][0][bcc]": ""
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
