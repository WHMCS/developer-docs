+++
title = "Module"
weight = 10

+++

The following hooks are provided for Module related events.

## AfterModule

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| failureResponseMessage | | |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModule', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleChangePassword

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | | |
| oldpassword | | |
| newpassword | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaProductDetailsPreModuleTemplate

Executes when rendering the client area product details page prior to module template invokation allowing to define additional template parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |
| groupname | string |  |
| product | string |  |
| modulename | string |  |
| domain | string |  |
| systemStatus | string |  |
| username | string |  |
| password | string |  |

#### Response

Return an array of template parameters to make available to the template.

#### Example Code

```
<?php
add_hook('ClientAreaProductDetailsPreModuleTemplate', 1, function($vars) {
    // Perform hook code here...
});
```

## OverrideModuleUsernameGeneration

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('OverrideModuleUsernameGeneration', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModule

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreModule', 1, function($vars) {
    // Perform hook code here...
});
```

