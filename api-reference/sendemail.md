+++
title = "SendEmail"
toc = true
+++

Send a client Email Notification

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "SendEmail" | Required |
| messagename | string | The name of the client email template to send | Optional |
| id | int | The related id for the type of email template. Eg this should be the client id for a general type email | Optional |
| customtype | string | The type of custom email template to send ('general', 'product', 'domain', 'invoice', 'support', 'affiliate') | Optional |
| custommessage | string | The HTML message body to send for a custom email | Optional |
| customsubject | string | The subject to send for a custom email | Optional |
| customvars | array | The custom variables to provide to the email template. Can be used for existing and custom emails. | Optional |

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
            'action' => 'SendEmail',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'messagename' => 'Client Signup Email',
            'id' => '1',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'SendEmail';
$postData = array(
    'messagename' => 'Client Signup Email',
    'id' => '1',
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

* You must provide either an existing email template name or a custom message type
* Invalid message type provided
* A subject is required for a custom message
* A message body is required for a custom message
* A related ID is required
* Email Template not found
* Email Template is disabled
* Sending Failed. Please see documentation.


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
