+++
title = "Service"
weight = 10

+++

The following hooks are provided for Service related events.

## AdminClientServicesTabFields

Executes when a service is being viewed in the Admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | the id of the service being loaded |

#### Response

An array of key -> value parameters to output additional fields as required.

#### Example Code

```
<?php
add_hook('AdminClientServicesTabFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientServicesTabFieldsSave

Executes when the Services tab in the Admin area is being saved. Receives all the $_REQUEST parameters as variables.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

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

Executes as the service is being saved, after any changes have been made.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| serviceid | int |  |

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

Executes as the service is being saved, before any changes have been made.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |

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

Executes as the service is being saved, before any changes have been made.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |

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

Executes when a service is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| serviceid | int |  |

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

Executes as the service is being saved, after any changes have been made.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| serviceid | int |  |

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

