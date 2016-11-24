+++
title = "Client Area Interface"
weight = 10

+++

The following hooks are provided for Client Area Interface related events.

## ClientAreaPageLogin

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $this->templatevars | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaPageLogin', 1, function($vars) {
    // Perform hook code here...
});
```

