+++
title = "AddClient"
toc = true
+++

Adds a client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddClient" | Required |
| firstname | string |  | Required |
| lastname | string |  | Required |
| companyname | string |  | Optional |
| email | string |  | Required |
| address1 | string |  | Required |
| address2 | string |  | Optional |
| city | string |  | Required |
| state | string |  | Required |
| postcode | string |  | Required |
| country | string | 2 character ISO country code | Required |
| phonenumber | string |  | Required |
| password2 | string |  | Required |
| securityqid | int | Security Question ID from tbladminsecurityquestions | Optional |
| securityqans | string | Security Question Answer | Optional |
| cardtype | string | Credit card type. Provide full name: Visa, Mastercard, American Express, etc... | Optional |
| cardnum | string | Credit card number | Optional |
| expdate | string | Format: MMYY | Optional |
| startdate | string | Format: MMYY (if applicable) | Optional |
| issuenumber | string | Credit card issue number (if applicable) | Optional |
| cvv | string | Credit card CVV number (will not be stored) | Optional |
| currency | int | Currency ID from tblcurrencies | Optional |
| groupid | int | Client Group ID from tblclientgroups | Optional |
| customfields | string | Base64 encoded serialized array of custom field values | Optional |
| language | string | Default language setting. Provide full name: 'english', 'french', etc... | Optional |
| clientip | string | IP address of the user | Optional |
| notes | string | Admin only notes | Optional |
| noemail | bool | Pass as true to skip sending welcome email | Optional |
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
            'cardtype' => 'Visa',
            'cardnum' => '4111111111111111',
            'expdate' => '0721',
            'clientip' => '1.2.3.4',
            'responsetype' => 'json',
        )
    )
);
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
    'cardtype' => 'Visa',
    'cardnum' => '4111111111111111',
    'expdate' => '0721',
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


### Error Responses

Possible error condition responses include:

* You did not enter your first name
* You did not enter your last name
* You did not enter your email address
* The email address you entered was not valid
* You did not enter your email address
* You did not enter your  address line 1
* You did not enter your city
* You did not enter your state
* You did not enter your postcode
* You did not enter your country
* You did not enter your phone number
* Invalid telephone phone number
* You did not provide required custom field value for


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
