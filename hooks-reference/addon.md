+++
title = "Addon"
weight = 10

+++

The following hooks are provided for Addon related events.

## AddonActivation

Executes when a product addon becomes active as part of invoice payment or order acceptance, following any provisioning or welcome email automation.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int | An alias for $clientid maintained for backwards compatibility |
| clientid | int | The client associated with the addon's service |
| serviceid | int | The product service the addon is being activated for (tblhosting) |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonActivation', 1, function($vars) {
    // Perform hook code here...
});
```

