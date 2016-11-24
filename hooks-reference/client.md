+++
title = "Client"
weight = 10

+++

The following hooks are provided for Client related events.

## AdminAreaClientSummaryActionLinks

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaClientSummaryActionLinks', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminAreaClientSummaryPage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaClientSummaryPage', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientFileUpload

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |
| title | | |
| filename | | |
| origfilename | | |
| adminonly | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientFileUpload', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientProfileTabFields

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $clientsdetails | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientProfileTabFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientProfileTabFieldsSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $_REQUEST | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientProfileTabFieldsSave', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterClientMerge

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| toUserID | | |
| fromUserID | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterClientMerge', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAlert

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAlert', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaHomepage

Executes on rendering of the client area homepage.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

Return HTML to be output on the page.

#### Example Code

```
<?php
add_hook('ClientAreaHomepage', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaHomepagePanels

Executes prior to rendering the Client Area Homepage panels. This can be used to manipulate and add additional panels. For more information on working with Homepage Panels, and further examples, please see Working with ClientArea Homepage Panels

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| item | \MenuItem |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaHomepagePanels', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaNavbars

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  null | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaNavbars', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPrimaryNavbar

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $primaryNavbar | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaPrimaryNavbar', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPrimarySidebar

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $primarySidebar | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaPrimarySidebar', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaProductDetails

Executes when the product details page is loaded within the client area. This hook runs regardless of service status, so be sure to check for the appropriate statuses if required.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| service | \Service | A service object representing the service being rendered. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaProductDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaRegister

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaRegister', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaSecondaryNavbar

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $secondaryNavbar | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaSecondaryNavbar', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaSecondarySidebar

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $secondarySidebar | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaSecondarySidebar', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaSidebars

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  null | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaSidebars', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientChangePassword

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |
| password | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientClose

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientClose', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientDelete

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientEdit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookValues | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientEmailVerificationComplete

Executes upon successful completion of email verification by a client user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userId | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientEmailVerificationComplete', 1, function($vars) {
    // Perform hook code here...
});
```

## PreDeleteClient

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreDeleteClient', 1, function($vars) {
    // Perform hook code here...
});
```

