+++
title = "Service"
weight = 10

+++

The following hooks are provided for Service related events.

## AdminClientServicesTabFields

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientServicesTabFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientServicesTabFieldsSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $_REQUEST | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientServicesTabFieldsSave', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminServiceEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $serviceDetails | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminServiceEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## CancellationRequest

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |
| relid | | |
| reason | | |
| type | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CancellationRequest', 1, function($vars) {
    // Perform hook code here...
});
```

## PreAdminServiceEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreAdminServiceEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## PreServiceEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreServiceEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ServiceDelete

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $serviceDetails | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServiceDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ServiceEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $serviceDetails | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServiceEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ServiceRecurringCompleted

Executes when the Recurring Cycles Limit is reached for a product.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |
| recurringinvoices | int | The total count of invoices generated |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServiceRecurringCompleted', 1, function($vars) {
    // Perform hook code here...
});
```

