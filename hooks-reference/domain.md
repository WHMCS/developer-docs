+++
title = "Domain"
weight = 10

+++

The following hooks are provided for Domain related events.

## DomainDelete

Executes when a service is being deleted.

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

Executes as the domain is being saved, before any changes have been made.

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
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

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

