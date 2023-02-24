+++
title = "Service"
weight = 10

+++

The following hooks are provided for Service related events.

## ServiceDelete

Executes when the Service has been deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int | An alias for $clientId maintained for backwards compatibility |
| clientId | int | The client associated with the service |
| serviceid | int | The product service ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServiceDelete', 1, function($vars) {
    // Perform hook code here...
});
```

