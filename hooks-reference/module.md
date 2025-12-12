+++
title = "Module"
weight = 10

+++

The following hooks are provided for Module related events.

## AddonModuleConfigSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonModuleConfigSave', 1, function($vars) {
    // Perform hook code here...
});
```

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
| newpassword | string |  |

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

## AfterModuleCustom

Executes upon successful completion of the module custom function.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleCustom', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleCustomFailed

Executes upon failure of the module custom function to complete successfully. The failure reason is provided in the input parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |
| failureResponseMessage | string | The failure reason error string returned by the provisioning module. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterModuleCustomFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleDeprovisionAddOnFeature

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
add_hook('AfterModuleDeprovisionAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleDeprovisionAddOnFeatureFailed

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
add_hook('AfterModuleDeprovisionAddOnFeatureFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleProvisionAddOnFeature

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
add_hook('AfterModuleProvisionAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleProvisionAddOnFeatureFailed

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
add_hook('AfterModuleProvisionAddOnFeatureFailed', 1, function($vars) {
    // Perform hook code here...
});
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

## AfterModuleSuspendAddOnFeature

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
add_hook('AfterModuleSuspendAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleSuspendAddOnFeatureFailed

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
add_hook('AfterModuleSuspendAddOnFeatureFailed', 1, function($vars) {
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

## AfterModuleUnsuspendAddOnFeature

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
add_hook('AfterModuleUnsuspendAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterModuleUnsuspendAddOnFeatureFailed

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
add_hook('AfterModuleUnsuspendAddOnFeatureFailed', 1, function($vars) {
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

## PreModuleCustom

Executes prior to the module custom function being run for a service. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in account creation. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleCustom', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleDeprovisionAddOnFeature

Executes prior to the module deprovision function being run for a Add-On Feature. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in feature deprovisioning. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleDeprovisionAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleProvisionAddOnFeature

Executes prior to the module provision function being run for an Add-On Feature. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in the feature provision. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleProvisionAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

## PreModuleRenew

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
add_hook('PreModuleRenew', 1, function($vars) {
    // Perform hook code here...
});
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

## PreModuleSuspendAddOnFeature

Executes prior to the module suspend function being run for an Add-On Feature. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in feature suspension. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleSuspendAddOnFeature', 1, function($vars) {
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

## PreModuleUnsuspendAddOnFeature

Executes prior to the module unsuspend function being run for an Add-On Feature. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/provisioning-modules/module-parameters/ |

#### Response

Accepts a return of key/value pairs to override the parameters to be used in feature unsuspension. Use the same names as the input parameters. Return `abortcmd=true` to abort the action.

#### Example Code

```
<?php
add_hook('PreModuleUnsuspendAddOnFeature', 1, function($vars) {
    // Perform hook code here...
});
```

