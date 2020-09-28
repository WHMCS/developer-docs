+++
next = "/advanced/db-interaction/"
prev = "/advanced/creating-pages/"
title = "Authentication via CurrentUser"
weight = 20

+++

`WHMCS\Authentication\CurrentUser` lets you assess the current state of authentication for the currently-logged-in user.

{{% notice info %}}
WHMCS 8.0 added this functionality.
{{% /notice %}}

## Methods

The sample code below returns the authentication status for the person who is viewing the page containing that code. Note that none of these authentication states are mutually exclusive; it is possible (and sometimes likely) for the current user to return [Admin, User, and client account states](https://docs.whmcs.com/Users_and_Accounts) simultaneously.

### isAuthenticatedUser()

Returns a Boolean value indicating whether the current user is authenticated as a User.

For example, this:

```
<?php

$currentUser = new \WHMCS\Authentication\CurrentUser;
if ($currentUser->isAuthenticatedUser()) {
    echo "Current user authenticated as User.";
} else {
    echo "Current user not authenticated as User.";
}
```

Could return:

```
Current user not authenticated as User.
```


### isAuthenticatedAdmin()

Returns a Boolean value indicating whether the current user is authenticated as an Admin.

For example, this:

```
<?php

$currentUser = new \WHMCS\Authentication\CurrentUser;
if ($currentUser->isAuthenticatedAdmin()) {
    echo "Current user is authenticated as Admin.";
} else {
    echo "Current user is not authenticated as Admin.";
}
```

Could return:

```
Current user is not authenticated as Admin.
```

### isMasqueradingAdmin()

Returns a Boolean value indicating whether the current user is authenticated as an Admin who is acting on behalf of a user. This occurs after an Admin clicks *Login as Owner* in the client profile.

For example, this:

```
<?php

$currentUser = new \WHMCS\Authentication\CurrentUser;
if ($currentUser->isMasqueradingAdmin()) {
    echo "Current user is a masquerading Admin.";
} else {
    echo "Current user is not a masquerading Admin.";
}
```

Could return:

```
Current user is a masquerading Admin.
```

### user()

Returns a `WHMCS\User\User` object that indicates the currently-authenticated User. You can use this according to the class documentation.

This returns `null` if the current user isn't authenticated as a User.

For example, this:

```
<?php

$currentUser = new \WHMCS\Authentication\CurrentUser;
$user = $currentUser->user();
if ($user) {
    echo "There is an authenticated User, and their name is {$user->fullName}.";
} else {
    echo "There is not an authenticated User.";
}
```

Could return:

```
There is an authenticated User, and their name is Jane Doe.
```

### admin()

Returns a `WHMCS\User\Admin` object that indicates the currently-authenticated Admin. You can action on this according to the class documentation.

This returns `null` if the current user isn't authenticated in the Admin Area (for example, if they are a User).

For example, this:

```
<?php

$currentUser = new \WHMCS\Authentication\CurrentUser;
$admin = $currentUser->admin();
if ($admin) {
    echo "There is an authenticated Admin, and their name is {$admin->fullName}.";
} else {
    echo "There is not an authenticated Admin.";
}
```

Could return:

```
There is an authenticated Admin, and their name is Jane Doe.
```

### client()

Returns a `WHMCS\User\Client` object that indicates the currently-authenticated client account. You can action on this according to the class documentation.

This returns `null` if the current user isn't authenticated as a client account (for example, if they are not authenticated in the Client Area).

For example, this:

```
<?php

$currentUser = new \WHMCS\Authentication\CurrentUser;
$client = $currentUser->client();
if ($client) {
    echo "There is an authenticated Client, and their name is {$client->fullName}.";
} else {
    echo "There is not an authenticated Client.";
}
```

Could return:

```
There is an authenticated Client, and their name is Jane Doe.
```
