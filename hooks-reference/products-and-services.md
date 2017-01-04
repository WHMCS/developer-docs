+++
title = "Products and Services"
weight = 10

+++

The following hooks are provided for Products and Services related events.

## AdminProductConfigFields

Executes as a product is being edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int |  |

#### Response

An array of key -> value pairs to display on the Other tab.

#### Example Code

```
<?php
add_hook('AdminProductConfigFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminProductConfigFieldsSave

Executes as a product is being saved. Access The Request variables to save custom config fields.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int |  |

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

Executes a product is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int |  |

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

Undocumented

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

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

Executes as a server is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | int |  |

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

Executes as a server is being edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerEdit', 1, function($vars) {
    // Perform hook code here...
});
```

