+++
title = "Module"
weight = 10

+++

The following hooks are provided for Module related events.

## AfterModuleChangePackage

Executes upon successful completion of the module function.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleChangePackage', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleChangePackageFailed

Executes upon failure of the module function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleChangePackageFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleChangePassword

Executes upon successful completion of a remote module API password change.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |
| oldpassword | string |  |
| newspassword | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleChangePasswordFailed

Executes upon failure of the module function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleChangePasswordFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleCreate

Executes upon successful completion of the module function.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleCreate', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleCreateFailed

Executes upon failure of the module function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleCreateFailed', 1, function($vars)
    {
        // Fetch failure response message & module parameters
        $failureResponseMessage = $vars['failureResponseMessage'];
        $moduleParameters = $vars['params'];

        // Execute your post failure code here
    }
);
```

## AfterModuleSuspend

Executes upon successful completion of the module function.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleSuspend', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleSuspendFailed

Executes upon failure of the module function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleSuspendFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleTerminate

Executes upon successful completion of the module function.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleTerminate', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleTerminateFailed

Executes upon failure of the module function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleTerminateFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleUnsuspend

Executes upon successful completion of the module function.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleUnsuspend', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleUnsuspendFailed

Executes upon failure of the module function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleUnsuspendFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## OverrideModuleUsernameGeneration

Executes as a username is being generated on module creation.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | The parameters being passed to the module function call |

#### Response

Return the new username to be used.

#### Example Code

```
<?php
add_hook('OverrideModuleUsernameGeneration', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleChangePackage

Executes prior to the module change package function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account upgrade or downgrade. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleChangePackage', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleChangePassword

Executes prior to the module change password function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account password reset. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleCreate

Executes prior to the module create function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account creation. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleCreate', 1, function($vars)
    {
        return array(
            'abortcmd' => true,
        );
    }
);
```

## PreModuleSuspend

Executes prior to the module suspend function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account suspension. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleSuspend', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleTerminate

Executes prior to the module terminate function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account termination. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleTerminate', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleUnsuspend

Executes prior to the module unsuspend function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account unsuspension. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleUnsuspend', 1, function($vars) {
    // Perform hook code here...
});
```

