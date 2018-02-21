+++
title = "GetTicketPredefinedReplies"
toc = true
+++

Obtain the Predefined Ticket Replies

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTicketPredefinedReplies" | Required |
| catid | int | Obtain predefined replies for a specific category id | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results returned |
| predefinedreplies | array | An array of predefined replies |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTicketPredefinedReplies',
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
$command = 'GetTicketPredefinedReplies';
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
    "totalresults": "4",
    "predefinedreplies": {
        "predefinedreply": [
            {
                "name": "Sample Quick Reference Reply",
                "reply": "Hello [NAME],\r\n\r\nUt faucibus malesuada diam, in commodo turpis eleifend vel. Proin nec dui ipsum. Aenean viverra.\r\n\r\n"
            },
            {
                "name": "Sample Sales Reply",
                "reply": "Hello [NAME],\r\n\r\nCras eget tellus lacinia, rhoncus lectus iaculis, venenatis risus. Nunc quam lectus, pulvinar a lectus.\r\n\r\n"
            },
            {
                "name": "Sample Sub-Support 1 Reply",
                "reply": "Hello [NAME],\r\n\r\nMaecenas et vulputate magna. Mauris ac mi odio. Nam vel lacinia dolor. Suspendisse eu orci.\r\n\r\n"
            },
            {
                "name": "Sample Support Reply",
                "reply": "Hello [NAME],\r\n\r\nUt fringilla congue velit, vitae bibendum lorem. Nullam convallis arcu nec felis interdum eleifend. Fusce.\r\n\r\n"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
