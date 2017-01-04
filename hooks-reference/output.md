+++
title = "Output"
weight = 10

+++

The following hooks are provided for Output related events.

## AdminAreaFooterOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookvars | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaFooterOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminAreaHeadOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookvars | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaHeadOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminAreaHeaderOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookvars | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaHeaderOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminInvoicesControlsOutput

Allows returning of output for display on the invoice edit page

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int |  |
| userid | int |  |
| subtotal | float |  |
| tax | float |  |
| tax2 | float |  |
| credit | float |  |
| total | float |  |
| balance | float |  |
| taxrate | float |  |
| taxrate2 | float |  |
| paymentmethod | string |  |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('AdminInvoicesControlsOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaDomainDetailsOutput

Allows returning of output for display in the client area domain details page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | \Domain | A domain object representing the domain being rendered. |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('ClientAreaDomainDetailsOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaFooterOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookParameters | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaFooterOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaHeadOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookParameters | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaHeadOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaHeaderOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookParameters | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaHeaderOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaProductDetailsOutput

Allows returning of output for display in the client area product details page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| service | \Service | A service object representing the service being rendered. |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('ClientAreaProductDetailsOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ReportViewPostOutput

Executes as a report is being displayed, after the output occurs

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| report | string |  |
| moduleType | string |  |
| moduleName | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ReportViewPostOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ReportViewPreOutput

Executes as a report is being displayed, before the output occurs

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| report | string |  |
| moduleType | string |  |
| moduleName | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ReportViewPreOutput', 1, function($vars) {
    // Perform hook code here...
});
```

