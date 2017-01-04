+++
title = "Domain"
weight = 10

+++

The following hooks are provided for Domain related events.

## AdminClientDomainsTabFields

Executes when a domain is being viewed in the Admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | the id of the domain being loaded |

#### Response

An array of key -> value parameters to output additional fields as required.

#### Example Code

```
<?php
add_hook('AdminClientDomainsTabFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientDomainsTabFieldsSave

Executes when the Domains tab in the Admin area is being saved. Receives all the $_REQUEST parameters as variables.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

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

