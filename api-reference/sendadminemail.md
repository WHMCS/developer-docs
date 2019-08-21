+++
title = "SendAdminEmail"
toc = true
+++

Send an Admin Email Notification

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "SendAdminEmail" | Required |
| messagename | string | The name of the admin email template to send | Optional |
| custommessage | string | The HTML message body to send for a custom email | Optional |
| customsubject | string | The subject to send for a custom email | Optional |
| type | string | Which type of admin notification will be send ('system', 'account', 'support') | Optional |
| deptid | int | The Id of the department the notification is for if 'support' $type | Optional |
| mergefields | array | The merge fields to be used in the email template | Optional |

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
            'action' => 'SendAdminEmail',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'messagename' => 'Service Unsuspension Successful',
            'mergefields' => array('client_id' => 1, 'service_id' => 1, 'service_product' => 'This is a product', 'service_domain' => 'sampledomain.com'),
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
$command = 'SendAdminEmail';
$postData = array(
    'messagename' => 'Service Unsuspension Successful',
    'mergefields' => array('client_id' => 1, 'service_id' => 1, 'service_product' => 'This is a product', 'service_domain' => 'sampledomain.com'),
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

* Email Template not found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
