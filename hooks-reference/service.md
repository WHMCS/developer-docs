+++
title = "Service"
weight = 10

+++

The following hooks are provided for Service related events.

## CancellationRequest

Executes as a cancellation request is being created

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| relid | int | The id of the service being cancelled |
| reason | string |  |
| type | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CancellationRequest', 1, function($vars) {
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

## ServiceEdit

Executes when the Service has been edited. After the changes have been made.

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

