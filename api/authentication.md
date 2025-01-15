+++
next = "/api/internal-api"
prev = "/api/getting-started"
title = "Authentication"
toc = true
weight = 20

+++

Use of the API requires API Authentication Credentials.  As well, the associated admin user must have the `API Access` permission granted to their admin role group.

API Authentication Credentials can be generated for an admin user within the Admin area as described in the [WHMCS Documentation](http://docs.whmcs.com/API_Authentication_Credentials).

Authentication is required for each API request.

## Authenticating with API Credentials

API requests will be authenticated based on the request parameters `identifier` and `secret` as provisioned when [Creating Admin API Authentication Credentials](http://docs.whmcs.com/API_Authentication_Credentials#Creating_Admin_API_Authentication_Credentials) within the WHMCS Admin Area.

```
$api_identifier = 'D4j1dKYE3g40VROOPCGyJ9zRwP0ADJIv';
$api_secret = 'F1CKGXRIpylMfsrig3mwwdSdYUdLiFlo';

$postfields = array(
    'identifier' => $api_identifier,
    'secret' => $api_secret,
    'action' => $api_call,
    'responsetype' => $response_type,
);
```

For forwards compatibility with existing integrations, the `identifier` and `secret` may also be passed in the `username` and `password` fields respectively. A valid identifier and secret combination passed in this way will also result in successful authentication.

## Authenticating with Login Credentials

Prior to WHMCS version 7.2, authentication was validated based on admin login credentials, and not API Authentication Credentials.
This method of authentication is still supported for backwards compatibility but may be deprecated in a future version of WHMCS.

To authenticate with the admin login credentials, pass the admin `username` and the MD5 hashed value of the respective admin's `password`.

```
$username = "your_admin_login_username";
$password = "your_admin_login_password";

$postfields = array(
    'username' => $username,
    'password' => md5($password),
    'action' => $api_call,
    'responsetype' => $response_type,
);
```
