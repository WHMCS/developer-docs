+++
title = "AddClient"
toc = true
+++

Adds a client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddClient" | Required |
| owner_user_id | int | The ID of the user that should own the client. Optional. When not provided, a new user will be created. | Optional |
| firstname | string | First name of the client to be created. Also used for the first name of the user when `owner_user_id` is not specified. | Required |
| lastname | string | Last name of the client to be created. Also used for the last name of the user when `owner_user_id` is not specified. | Required |
| companyname | string |  | Optional |
| email | string | Email address of the client to be created. Also used for the email of the user when `owner_user_id` is not specified. | Required |
| address1 | string |  | Required |
| address2 | string |  | Optional |
| city | string |  | Required |
| state | string |  | Required |
| postcode | string |  | Required |
| country | string | 2 character ISO country code. | Required |
| phonenumber | string |  | Required |
| tax_id | string | The client's tax ID. | Optional |
| password2 | string | The password for the newly-created user account. Required when `owner_user_id` is not specified. | Optional |
| securityqid | int | The ID of the security question in `tbladminsecurityquestions`. Required when `owner_user_id` is not specified. | Optional |
| securityqans | string | The security question answer for a newly-created user. | Optional |
| currency | int | Currency ID from `tblcurrencies`. | Optional |
| groupid | int | Client Group ID from `tblclientgroups`. | Optional |
| customfields | string | Base64 encoded serialized array of custom field values. | Optional |
| language | string | Default language setting. Also used for the language of the user when `owner_user_id` is not specified. Provide the full name: 'english', 'french', etc.... | Optional |
| clientip | string | The originating IP address for the request. | Optional |
| notes | string | Admin only notes. | Optional |
| marketingoptin | bool | Whether the client should opt-in to receiving marketing emails. | Optional |
| noemail | bool | Whether to send the client a welcome email. A true value will not send the email. | Optional |
| skipvalidation | bool | Whether to enforce required fields. A true value will not enforce required fields. This does not apply to `email` and `password2` when `owner_user_id` is not specified. | Optional |
| ~~cardtype~~ | ~~string~~ | ~~Credit card type. Provide full name: Visa, Mastercard, American Express, etc....~~ | Deprecated |
| ~~cardnum~~ | ~~string~~ | ~~Credit card number.~~ | Deprecated |
| ~~expdate~~ | ~~string~~ | ~~Format: MMYY.~~ | Deprecated |
| ~~startdate~~ | ~~string~~ | ~~Format: MMYY (if applicable).~~ | Deprecated |
| ~~issuenumber~~ | ~~string~~ | ~~Credit card issue number (if applicable).~~ | Deprecated |
| ~~cvv~~ | ~~string~~ | ~~Credit card CVV number (will not be stored).~~ | Deprecated |

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
            'action' => 'AddClient',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'firstname' => 'John',
            'lastname' => 'Doe',
            'email' => 'john.doe@example.com',
            'address1' => '123 Main Street',
            'city' => 'Anytown',
            'state' => 'State',
            'postcode' => '12345',
            'country' => 'US',
            'phonenumber' => '800-555-1234',
            'password2' => 'password',
            'clientip' => '1.2.3.4',
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
$command = 'AddClient';
$postData = array(
    'firstname' => 'John',
    'lastname' => 'Doe',
    'email' => 'john.doe@example.com',
    'address1' => '123 Main Street',
    'city' => 'Anytown',
    'state' => 'State',
    'postcode' => '12345',
    'country' => 'US',
    'phonenumber' => '800-555-1234',
    'password2' => 'password',
    'clientip' => '1.2.3.4',
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

* Credit card related parameters are now deprecated and may be removed in a future version. Use AddPayMethod instead.


### Error Responses

Possible error condition responses include:

* Invalid Owner User ID
* You did not enter your first name
* You did not enter your last name
* You did not enter your email address
* The email address you entered was not valid
* You did not enter your email address
* You did not enter your  address line 1
* You did not enter your city
* You did not enter your state
* You did not enter your postcode
* Valid country required
* You did not enter your phone number
* Invalid telephone phone number
* You did not provide required custom field value for
* The email address entered is not available for use.
* A user already exists with that email address


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Added `tax_id` parameter. |
| 7.8 | Credit card related parameters are now deprecated and may be removed in a future version. Use AddPayMethod instead. |
| 8.0 | Added 'owner_user_id' parameter. |
