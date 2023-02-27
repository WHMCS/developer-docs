+++
title = "Domain"
weight = 10

+++

The following hooks are provided for Domain related events.

## DomainDelete

Executes when a domain is being deleted from the client account.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| domainid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DomainDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## DomainEdit

Executes when the domain is being edited via the Client Profile Summary and Domains tabs in the Admin Area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| domainid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DomainEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## DomainTransferCompleted

Executes when a domain transfer is set to completed by the domain sync cron.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domainId | int | The unique identifier for the domain |
| domain | string | The domain name |
| registrationPeriod | string | The registration period |
| expiryDate | string | The expiry date (if returned by the registrar) |
| registrar | string | The registrar used |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DomainTransferCompleted', 1, function($vars) {
    // Perform hook code here...
});
```

## DomainTransferFailed

Executes when a domain transfer is set to failed by the domain sync cron.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domainId | int | The unique identifier for the domain |
| domain | string | The domain name |
| registrationPeriod | string | The registration period |
| expiryDate | string | The expiry date (if returned by the registrar) |
| registrar | string | The registrar used |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DomainTransferFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## DomainValidation

Executes as domain validation is being run

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| sld | string | The sld of the domain. eg whmcs in whmcs.com |
| tld | string | The tld of the domain. eg com in whmcs.com |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DomainValidation', 1, function($vars) {
    // Perform hook code here...
});
```

## PreDomainRegister

Executes before a domain register command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | string | The domain being registered |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreDomainRegister', 1, function($vars) {
    // Perform hook code here...
});
```

## PreDomainTransfer

Executes before a domain transfer command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreDomainTransfer', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarRegisterDomain

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
add_hook('PreRegistrarRegisterDomain', 1, function($vars)
    {
        $domainName = $vars['params']['sld'] . '.' . $vars['params']['tld'];

        return array(
            'abortWithError' => 'Error message to display goes here',
        );

        //return array(
        //    'abortWithSuccess' => true,
        //);
    }
);
```

## PreRegistrarRenewDomain

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
add_hook('PreRegistrarRenewDomain', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarTransferDomain

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
add_hook('PreRegistrarTransferDomain', 1, function($vars) {
    // Perform hook code here...
});
```

## TopLevelDomainAdd

Executes when a new domain extension is added.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| tld | string |  |
| supportsDnsManagement | bool |  |
| supportsEmailForwarding | bool |  |
| supportsIdProtection | bool |  |
| requiresEppCode | bool |  |
| automaticRegistrar | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TopLevelDomainAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## TopLevelDomainDelete

Executes when a domain extension is deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| tld | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TopLevelDomainDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## TopLevelDomainPricingUpdate

Executes when domain extension pricing is updated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| tld | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TopLevelDomainPricingUpdate', 1, function($vars) {
    // Perform hook code here...
});
```

## TopLevelDomainUpdate

Executes when domain extensions configuration is updated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| modifiedTlds | string[] | An array of domain extensions that have been modified. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TopLevelDomainUpdate', 1, function($vars) {
    // Perform hook code here...
});
```

