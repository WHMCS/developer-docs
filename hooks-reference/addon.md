+++
title = "Addon"
weight = 10

+++

The following hooks are provided for Addon related events.

## AddonActivated

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonActivated', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonActivation

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonActivation', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonAdd

Executes when an addon is added to a product/service.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonCancelled

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonCancelled', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonConfig

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonConfig', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonConfigSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonConfigSave', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonDeleted

We don't pass all the details for the AddonDeleted hook

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonDeleted', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonSuspended

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonSuspended', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonTerminated

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonTerminated', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonUnsuspended

Executes when a product addon is being unsuspended and set to Active status.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonUnsuspended', 1, function($vars) {
    // Perform hook code here...
});
```

## LicensingAddonReissue

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| licenseid | | |
| id | | |
| array("serviceid | | |
| serviceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LicensingAddonReissue', 1, function($vars) {
    // Perform hook code here...
});
```

## LicensingAddonVerify

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| licenseid | | |
| serviceid | | |
| xmlresponse | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LicensingAddonVerify', 1, function($vars) {
    // Perform hook code here...
});
```

