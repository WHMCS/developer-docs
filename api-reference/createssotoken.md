+++
title = "CreateSsoToken"
toc = true
+++

Create a single use, client or user single sign-on access token

Tokens are valid for a maximum of 60 seconds.

WARNING: The token returned provides _complete_ authentication to the associated
client account.  It is _imperative_ that scripts ensure the actor who
triggers this API call and receives this data has verified their identity and
ownership for the associated account.  IE, the invocation of this API
should be behind your own user authentication and account mapping engine.

NOTE: The associated endpoint where this token is redeemed is only for one-time
trusted tokens and will not attempt to enforce captcha or 2FA authorization
controls common to the WHMCS login form.

A valid destination is expressed using the short term like "clientarea:services".
Possible destinations are documented at https://go.whmcs.com/1989/single-sign-on-customization

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateSsoToken" | Required |
| client_id | int | The id of the client that should be authenticated by the resulting token | Optional |
| user_id | int | The id of the user that should be authenticated by the resulting token. If not provided, the owner of the requested client will be assumed. | Optional |
| destination | string | A single valid destination. If not provided, the destination will be the clientarea homepage | Optional |
| service_id | int | The id of the service for respective clientarea $destination | Optional |
| domain_id | int | The id of the service for respective clientarea $destination | Optional |
| sso_redirect_path | string | Custom relative path for redirection after authentication when using sso:custom_redirect destination | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| access_token | string | A OTP token to authenticate the user at the single sign-on endpoint |
| redirect_url | string | A prepared URL for redirecting your remote system authenticated users |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'CreateSsoToken',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'client_id' => '1',
            'destination' => 'clientarea:product_details',
            'service_id' => '1',
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
$command = 'CreateSsoToken';
$postData = array(
    'client_id' => '1',
    'destination' => 'clientarea:product_details',
    'service_id' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "access_token": "afaed4482ad1e6b75492cdd421cc458b1991a97c",
    "redirect_url": "http:\/\/example.test\/oauth\/singlesignon.php?access_token=afaed4482ad1e6b75492cdd421cc458b1991a97c"
}
```


### Error Responses

Possible error condition responses include:

* Invalid client_id
* Invalid user_id
* Invalid user_id for client
* A valid client_id or user_id is required
* Invalid destination
* Token could not be provisioned: x
* SSO authentication blocked for client x


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.10.0 | Initial Version |
