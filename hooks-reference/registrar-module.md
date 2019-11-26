+++
title = "Registrar Module"
weight = 10

+++

The following hooks are provided for Registrar Module related events.

## AfterRegistrarGetContactDetails

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarGetContactDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarGetDNS

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarGetDNS', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarGetEPPCode

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarGetEPPCode', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarGetNameservers

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarGetNameservers', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRegister

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRegister', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRegistration

Executes after a successful domain register command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

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

Executes after a failed domain register command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| error | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRegistrationFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRenew

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRenew', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRenewal

Executes after a successful domain renewal command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

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

Executes after a failed domain renewal command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| error | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRenewalFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRequestDelete

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRequestDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarSaveContactDetails

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarSaveContactDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarSaveDNS

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarSaveDNS', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarSaveNameservers

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarSaveNameservers', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarTransfer

Executes upon completion of the registrar module function. Will execute regardless of success state.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array | An array of results returned from the registrar function call |
| functionExists | bool | Returns true if the registrar module supports the given action |
| functionSuccessful | bool | Returns true if the registrar function completed without error |

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

Executes after a failed domain transfer command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| error | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarTransferFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarGetContactDetails

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarGetContactDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarGetDNS

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarGetDNS', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarGetEPPCode

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarGetEPPCode', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarGetNameservers

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarGetNameservers', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarRequestDelete

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarRequestDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarSaveContactDetails

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarSaveContactDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarSaveDNS

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarSaveDNS', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarSaveNameservers

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarSaveNameservers', 1, function($vars) {
    // Perform hook code here...
});
```

