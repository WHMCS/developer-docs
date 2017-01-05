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

