+++
title = "User"
weight = 10

+++

The following hooks are provided for User related events.

## PreUserAdd

Executes just prior to a user being added to WHMCS. Changes to hook variables will not be honored.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| user_id | int | The id of the user that has been added |
| firstname | string |  |
| lastname | string |  |
| email | string |  |
| password | string |  |
| language | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreUserAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## UserAdd

Executes as a user is being added to WHMCS.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| user_id | int | The id of the user that has been added |
| firstname | string |  |
| lastname | string |  |
| email | string |  |
| password | string |  |
| language | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('UserAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## UserChangePassword

Executed when a change of password occurs for a user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int | The ID of the User being updated |
| password | string | The new password |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('UserChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## UserEdit

Executes when a user is edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| user_id | int |  |
| firstname | string |  |
| lastname | string |  |
| email | string |  |
| olddata | array | An array of the previous user information |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('UserEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## UserEmailVerificationComplete

Executes upon successful completion of email verification by a user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userId | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('UserEmailVerificationComplete', 1, function($vars) {
    // Perform hook code here...
});
```

