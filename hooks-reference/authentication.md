+++
title = "Authentication"
weight = 10

+++

The following hooks are provided for Authentication related events.

## ClientLogin

Executes when a client is logging into the Client Area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| contactid| int | optional|

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientLogin', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientLoginShare

Executes as part of client login if user does not exist.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| username | string |  |
| password | string |  |

#### Response

Return data to create a user or refer to an existing client to be logged in as. id for existing user, email, boolean create to create new user, firstname, lastname etc to create a client.

#### Example Code

```
<?php
add_hook('ClientLoginShare', 1, function($vars) {
    // Perform custom authentication logic here
    // There are 4 supported return values, each demonstrated below.

    // User not found
    return false;

    // Login as existing WHMCS Client ID
    return array(
        'id' => '123',
    );

    // Login as existing WHMCS Client by Email Address
    return array(
        'email' => 'demo@whmcs.com',
    );

    // Create a new client and login
    return array(
        'create' => true,
        'email' => 'demo@whmcs.com',
        'firstname' => 'Demo',
        'lastname' => 'User',
        'companyname' => 'Demo Company',
        'address1' => '123 Demo Street',
        'address2' => '',
        'city' => 'Demo',
        'state' => 'Demo',
        'postcode' => '12345',
        'country' => 'US',
        'phonenumber' => '11111111111',
        'password' => 'xxxxxxxx',
    );
});
```

## ClientLogout

Executes when a client is logging out of the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientLogout', 1, function($vars) {
    // Perform hook code here...
});
```

