+++
title = "Products and Services"
weight = 10

+++

The following hooks are provided for Products and Services related events.

## AdminProductConfigFields

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminProductConfigFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminProductConfigFieldsSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminProductConfigFieldsSave', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterProductUpgrade

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| upgradeid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterProductUpgrade', 1, function($vars) {
    // Perform hook code here...
});
```

## ProductDelete

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ProductDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ProductEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | | |
| $array | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ProductEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ServerAdd

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## ServerDelete

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ServerEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerEdit', 1, function($vars) {
    // Perform hook code here...
});
```

