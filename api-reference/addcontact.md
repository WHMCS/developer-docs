+++
title = "AddContact"
toc = true
+++

Adds a contact to a client account.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddContact" | Required |
| clientid | int |  | Required |
| firstname | string |  | Optional |
| lastname | string |  | Optional |
| companyname | string |  | Optional |
| email | string | Email address to identify the contact. This should be unique if the contact will be a sub-account | Optional |
| address1 | string |  | Optional |
| address2 | string |  | Optional |
| city | string |  | Optional |
| state | string |  | Optional |
| postcode | string |  | Optional |
| country | string | 2 character ISO country code | Optional |
| phonenumber | string |  | Optional |
| tax_id | string |  | Optional |
| password2 | string | if creating a sub-account | Optional |
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
| contactid | int | The id of the newly added contact. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddContact',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'firstname' => 'Jane',
            'lastname' => 'Doe',
            'email' => 'jane.doe@example.com',
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
$command = 'AddContact';
$postData = array(
    'clientid' => '1',
    'firstname' => 'Jane',
    'lastname' => 'Doe',
    'email' => 'jane.doe@example.com',
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

* Client ID Not Found
* Duplicate Email Address


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Added `tax_id` parameter. |
| 7.9 | Added `affiliateemails` parameter. |
| 7.10 | Added email preferences parameters |
