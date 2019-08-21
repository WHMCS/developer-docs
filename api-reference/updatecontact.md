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
| generalemails | bool | Should the contact receive general emails | Optional |
| productemails | bool | Should the contact receive product emails | Optional |
| domainemails | bool | Should the contact receive domain emails | Optional |
| invoiceemails | bool | Should the contact receive invoice emails | Optional |
| supportemails | bool | Should the contact receive support emails | Optional |
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


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
