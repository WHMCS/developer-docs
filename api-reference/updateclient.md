+++
title = "UpdateClient"
toc = true
+++

Updates a client with the passed parameters.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateClient" | Required |
| clientid | int | The id of the client to update | Optional |
| clientemail | string | The email address of the client to update. Either $clientid or $clientemail is required | Optional |
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
| password2 | string |  | Optional |
| securityqid | int | Security Question ID from tbladminsecurityquestions | Optional |
| securityqans | string | Security Question Answer | Optional |
| cardtype | string | Credit card type. Provide full name: Visa, Mastercard, American Express, etc... | Optional |
| cardnum | string | Credit card number | Optional |
| expdate | string | Format: MMYY | Optional |
| startdate | string | Format: MMYY (if applicable) | Optional |
| issuenumber | string | Credit card issue number (if applicable) | Optional |
| bankcode | string | Client Bank Account Code (if applicable) | Optional |
| bankacct | string | Client bank Account number (if applicable) | Optional |
| cvv | string | Credit card CVV number (will not be stored) | Optional |
| currency | int | Currency ID from tblcurrencies | Optional |
| groupid | int | Client Group ID from tblclientgroups | Optional |
| customfields | string | Base64 encoded serialized array of custom field values | Optional |
| language | string | Default language setting. Provide full name: 'english', 'french', etc... | Optional |
| clientip | string | IP address of the user | Optional |
| notes | string | Admin only notes | Optional |
| paymentmethod | string | The default payment method | Optional |
| marketingoptin | bool | Set true to opt client in to marketing emails | Optional |
| clearcreditcard | bool | Pass as true to clear the stored CC details | Optional |
| skipvalidation | bool | Pass as true to ignore required fields validation | Optional |

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
            'action' => 'UpdateClient',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'firstname' => 'John',
            'lastname' => 'Doe',
            'email' => 'john.doe@example.com',
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
$command = 'UpdateClient';
$postData = array(
    'clientid' => '1',
    'firstname' => 'John',
    'lastname' => 'Doe',
    'email' => 'john.doe@example.com',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "clientid": "1"
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
