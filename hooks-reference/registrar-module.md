+++
title = "Registrar Module"
weight = 10

+++

The following hooks are provided for Registrar Module related events.

## AfterRegistrar

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $vars | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrar', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRegistration

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRegistration', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRegistrationFailed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |
| error | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRegistrationFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRenewal

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRenewal', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRenewalFailed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |
| error | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRenewalFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarTransfer

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarTransfer', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarTransferFailed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |
| error | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarTransferFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrar

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreRegistrar', 1, function($vars) {
    // Perform hook code here...
});
```

