+++
title = "UpdateContact"
toc = true
+++

Updates a contact with the passed parameters.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateContact" | Required |
| contactid | int | The id of the contact to update | Required |
| firstname | string |  | Optional |
| lastname | string |  | Optional |
| companyname | string |  | Optional |
| email | string |  | Optional |
| address1 | string |  | Optional |
| address2 | string |  | Optional |
| city | string |  | Optional |
| state | string |  | Optional |
| postcode | string |  | Optional |
| country | string | 2 character ISO country code | Optional |
| phonenumber | string |  | Optional |
| email_preferences[general] | bool | Should the client receive general emails | Optional |
| email_preferences[product] | bool | Should the client receive product emails | Optional |
| email_preferences[domain] | bool | Should the client receive domain emails | Optional |
| email_preferences[invoice] | bool | Should the client receive invoice emails | Optional |
| email_preferences[support] | bool | Should the client receive support emails | Optional |
| email_preferences[affiliate] | bool | Should the client receive affiliate emails | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| contactid | int | The contact ID that was updated |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateContact',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'contactid' => '1',
            'firstname' => 'John',
            'lastname' => 'Doe',
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
$command = 'UpdateContact';
$postData = array(
    'contactid' => '1',
    'firstname' => 'John',
    'lastname' => 'Doe',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "contactid": "1"
}
```


### Warning Responses

Warning responses are returned when using API functionality that has been removed or marked as deprecated.
We suggest following any recommended actions in the warning to ensure future compatibility.

Possible warning messages include:

* Sub Accounts are no longer supported. Please use UpdateUser


### Error Responses

Possible error condition responses include:

* Contact ID Not Found
* Duplicate Email Address
* You must have at least one email address enabled to receive domain related notifications as required by ICANN. To disable domain notifications, please enable domain notifications for the primary account holder or another contact


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.10 | Added email preferences parameters |
| 8.0 | Removed sub-account functionality |
