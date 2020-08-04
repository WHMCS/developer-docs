+++
title = "User"
weight = 10

+++

The following hooks are provided for User related events.

## UserChangePassword

Executed when a change of password occurs for a user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
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

