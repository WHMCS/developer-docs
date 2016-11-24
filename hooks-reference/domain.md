+++
title = "Domain"
weight = 10

+++

The following hooks are provided for Domain related events.

## AdminClientDomainsTabFields

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientDomainsTabFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientDomainsTabFieldsSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $_REQUEST | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientDomainsTabFieldsSave', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaDomainDetails

Executes when the domain details page is loaded within the client area. This hook runs regardless of domain status, so be sure to check for the appropriate statuses if required.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | \Domain | A domain object representing the domain being rendered. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaDomainDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## DomainDelete

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $domainDetails | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $domainDetails | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| sld | | |
| tld | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreDomainTransfer', 1, function($vars) {
    // Perform hook code here...
});
```

