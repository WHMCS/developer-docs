+++
title = "Module"
weight = 10

+++

The following hooks are provided for Module related events.

## AfterModule

Executes after any standard service module function call has failed. Hook name is updated as appropriate.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| failureResponseMessage | string | The response message from the function call. |
| params | array | The parameters passed to the module function call. |

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

## OverrideModuleUsernameGeneration

Executes as a username is being generated on module creation.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | array | The parameters being passed to the module function call |

#### Response

Return the new username to be used. Eg: return array('newusername');

#### Example Code

```
<?php
add_hook('OverrideModuleUsernameGeneration', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModule

Executes before any standard service module function call. Hook name is updated as appropriate.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | The parameters passed to the module function call. |

#### Response

Return boolean abortcmd to stop the command being run. eg: return array('abortcmd' => true,);

#### Example Code

```
<?php
add_hook('PreModule', 1, function($vars) {
    // Perform hook code here...
});
```

