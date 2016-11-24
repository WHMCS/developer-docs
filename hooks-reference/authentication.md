+++
title = "Authentication"
weight = 10

+++

The following hooks are provided for Authentication related events.

## AdminLogout

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| adminid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminLogout', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientLogin

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientLogin', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientLogout

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientLogout', 1, function($vars) {
    // Perform hook code here...
});
```

