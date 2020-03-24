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
| subaccount | bool | Is the contact a subaccount | Optional |
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
| password2 | string | (sub-account only) | Optional |
| email_preferences[general] | bool | Should the client receive general emails | Optional |
| email_preferences[product] | bool | Should the client receive product emails | Optional |
| email_preferences[domain] | bool | Should the client receive domain emails | Optional |
| email_preferences[invoice] | bool | Should the client receive invoice emails | Optional |
| email_preferences[support] | bool | Should the client receive support emails | Optional |
| email_preferences[affiliate] | bool | Should the client receive affiliate emails | Optional |
| permissions | string | A comma separated list of sub-account permissions. eg manageproducts,managedomains | Optional |

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
