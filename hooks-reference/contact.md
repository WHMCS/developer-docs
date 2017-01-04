+++
title = "Contact"
weight = 10

+++

The following hooks are provided for Contact related events.

## ContactAdd

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| contactid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## ContactChangePassword

Executed when a change of password occurs for a contact.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| contactid | int |  |
| password | string | The new password |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ContactEdit

Undocumented

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactEdit', 1, function($vars) {
    // Perform hook code here...
});
```

