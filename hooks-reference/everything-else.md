+++
title = "Everything Else"
weight = 10

+++

The following hooks are provided for Everything Else related events.

## AdminAreaPage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $hookvars | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaPage', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminHomepage

Allows returning of output for display on the admin homepage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('AdminHomepage', 1, function($vars) {
    // Perform hook code here...
});
```

## AffiliateActivation

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affid | | |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AffiliateActivation', 1, function($vars) {
    // Perform hook code here...
});
```

## AffiliateClickthru

Executes when a user has clicked an affiliate referral link.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affiliateId | int | The unique id of the affiliate that the link belongs to |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AffiliateClickthru', 1, function($vars) {
    // Perform hook code here...
});
```

## AffiliateCommission

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affiliateId | | |
| referralId | | |
| serviceId | | |
| commissionAmount | | |
| commissionDelayed | | |
| clearingDate | | |
| payout | | |
| message | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AffiliateCommission', 1, function($vars) {
    // Perform hook code here...
});
```

## AffiliateWithdrawalRequest

Executes when an affiliate withdrawal request is submitted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affiliateId | int | The unique id of the affiliate making the request |
| userId | int | The user id of the user making the request |
| contactId | int | The contact id of the user making the request if logged in as a sub-account |
| balance | float | The amount of commission the withdrawal request is for |

#### Response

To skip creating a ticket for the request: return array('skipTicket' => true);

#### Example Code

```
<?php
add_hook('AffiliateWithdrawalRequest', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterConfigOptionsUpgrade

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| upgradeid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterConfigOptionsUpgrade', 1, function($vars) {
    // Perform hook code here...
});
```

## CCUpdate

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | | |
| cardtype | | |
| cardnum | | |
| cardcvv | | |
| expdate | | |
| cardstart | | |
| issuenumber | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CCUpdate', 1, function($vars) {
    // Perform hook code here...
});
```

## CalcAffiliateCommission

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affid | | |
| relid | | |
| amount | | |
| commission | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CalcAffiliateCommission', 1, function($vars) {
    // Perform hook code here...
});
```

## CustomFieldLoad

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| fieldid | | |
| relid | | |
| value | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CustomFieldLoad', 1, function($vars) {
    // Perform hook code here...
});
```

## CustomFieldSave

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| fieldid | | |
| relid | | |
| value | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CustomFieldSave', 1, function($vars) {
    // Perform hook code here...
});
```

## EmailPreLog

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $emailData | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('EmailPreLog', 1, function($vars) {
    // Perform hook code here...
});
```

## EmailPreSend

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| messagename | | |
| relid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('EmailPreSend', 1, function($vars) {
    // Perform hook code here...
});
```

## EmailTplMergeFields

Executes when editing an email template.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| type | string | The type of email template being edited. |

#### Response

an Array of key -> value pairs of merge fields

#### Example Code

```
<?php
add_hook('EmailTplMergeFields', 1, function($vars) {
    // Perform hook code here...
});
```

## FetchCurrencyExchangeRates

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $exchrate | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FetchCurrencyExchangeRates', 1, function($vars) {
    // Perform hook code here...
});
```

## IntelligentSearch

Executes as the Intelligent Search is being completed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| searchTerm | string |  |

#### Response

An array of additional responses to be appended to the search results.

#### Example Code

```
<?php
add_hook('IntelligentSearch', 1, function($vars) {
    // Perform hook code here...
});
```

## LinkTracker

Executes when a link.php link is being used.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| linkid | int | The id of the link being followed |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LinkTracker', 1, function($vars) {
    // Perform hook code here...
});
```

## LogActivity

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| description | | |
| user | | |
| userid | | |
| ipaddress | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LogActivity', 1, function($vars) {
    // Perform hook code here...
});
```

## PreAutomationTask

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| task | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreAutomationTask', 1, function($vars) {
    // Perform hook code here...
});
```

