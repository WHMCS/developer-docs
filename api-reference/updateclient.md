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
| tax_id | string | The client Tax ID | Optional |
| password2 | string |  | Optional |
| securityqid | int | Security Question ID from tbladminsecurityquestions | Optional |
| securityqans | string | Security Question Answer | Optional |
| ~~cardtype~~ | ~~string~~ | ~~Credit card type. Provide full name: Visa, Mastercard, American Express, etc...~~ | Deprecated |
| ~~cardnum~~ | ~~string~~ | ~~Credit card number~~ | Deprecated |
| ~~expdate~~ | ~~string~~ | ~~Format: MMYY~~ | Deprecated |
| ~~startdate~~ | ~~string~~ | ~~Format: MMYY (if applicable)~~ | Deprecated |
| ~~issuenumber~~ | ~~string~~ | ~~Credit card issue number (if applicable)~~ | Deprecated |
| ~~cvv~~ | ~~string~~ | ~~Credit card CVV number (will not be stored)~~ | Deprecated |
| ~~bankcode~~ | ~~string~~ | ~~Client Bank Account Code (if applicable)~~ | Deprecated |
| ~~bankacct~~ | ~~string~~ | ~~Client bank Account number (if applicable)~~ | Deprecated |
| currency | int | Currency ID from tblcurrencies | Optional |
| groupid | int | Client Group ID from tblclientgroups | Optional |
| customfields | string | Base64 encoded serialized array of custom field values | Optional |
| language | string | Default language setting. Provide full name: 'english', 'french', etc... | Optional |
| clientip | string | IP address of the user | Optional |
| notes | string | Admin only notes | Optional |
| status | string | Status, e.g. "Active" | Optional |
| paymentmethod | string | The default payment method | Optional |
| email_preferences[general] | bool | Should the client receive general emails | Optional |
| email_preferences[product] | bool | Should the client receive product emails | Optional |
| email_preferences[domain] | bool | Should the client receive domain emails | Optional |
| email_preferences[invoice] | bool | Should the client receive invoice emails | Optional |
| email_preferences[support] | bool | Should the client receive support emails | Optional |
| email_preferences[affiliate] | bool | Should the client receive affiliate emails | Optional |
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


### Warning Responses

Warning responses are returned when using API functionality that has been removed or marked as deprecated.
We suggest following any recommended actions in the warning to ensure future compatibility.

Possible warning messages include:

* Credit card related parameters are now deprecated and may be removed in a future version. Use AddPayMethod or UpdatePayMethod instead.
* Credit card related parameters are now deprecated and may be removed in a future version. Use DeletePayMethod instead.


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* You must have at least one email address enabled to receive domain related notifications as required by ICANN. To disable domain notifications, please create an alternative contact that is set to receive them
* Duplicate Email Address
* Multiple Credit Card Pay Methods Found
* Multiple Bank Account Pay Methods Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.10 | Added email preferences parameters |
| 7.8 | Credit card related parameters are now deprecated and may be removed in a future version. Use AddPayMethod, DeletePayMethod or UpdatePayMethod instead. |
