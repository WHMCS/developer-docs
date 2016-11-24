+++
title = "Shopping Cart"
weight = 10

+++

The following hooks are provided for Shopping Cart related events.

## AcceptOrder

Runs when an order is accepted prior to any acceptance actions being executed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The order ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AcceptOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonFraud

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| userid | | |
| serviceid | | |
| addonid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonFraud', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterFraudCheck

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $hookresults | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterFraudCheck', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterShoppingCartCheckout

Upon completion of checkout once the order has been created, invoice generated and all email notifications sent.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| OrderID | int | The Order ID |
| OrderNumber | int | The randomly generated order number |
| ServiceIDs | array | An array of Service IDs created by the order |
| AddonIDs | array | An array of Addon IDs created by the order |
| DomainIDs | array | An array of Domain IDs created by the order |
| RenewalIDs | array | An array of Domain Renewal IDs created by the order |
| PaymentMethod | string | The payment gateway selected |
| InvoiceID | int | The Invoice ID |
| TotalDue | float | The total amount due |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterShoppingCartCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## CancelOrder

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CancelOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## CartTotalAdjustment

Invoked as the order total is being calculated, this can be used to manipulate the final total.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| products | array | An indexed array of products in the shopping cart. Keys include `pid`, `domain`, `billingcycle`, `configoptions`, `customfields`, `addons`, `server`, `hostname` |
| domains | array | An indexed array of domain registrations & transfers in the shopping cart. Keys include `type`, `domain`, `regperiod` |

#### Response

Return an array consisting of adjustment `description`, `amount` and `taxed` (bool)

#### Example Code

```
<?php
add_hook('CartTotalAdjustment', 1, function($vars) {
    // Perform hook code here...
});
```

## DeleteOrder

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DeleteOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## FraudOrder

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FraudOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## OrderAddonPricingOverride

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| key | | |
| addonid | | |
| serviceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('OrderAddonPricingOverride', 1, function($vars) {
    // Perform hook code here...
});
```

## OrderProductPricingOverride

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| key | | |
| pid | | |
| proddata | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('OrderProductPricingOverride', 1, function($vars) {
    // Perform hook code here...
});
```

## OrderProductUpgradeOverride

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| 0 | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('OrderProductUpgradeOverride', 1, function($vars) {
    // Perform hook code here...
});
```

## OverrideOrderNumberGeneration

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| cart | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('OverrideOrderNumberGeneration', 1, function($vars) {
    // Perform hook code here...
});
```

## PendingOrder

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PendingOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## PreCalculateCartTotals

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| cart | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreCalculateCartTotals', 1, function($vars) {
    // Perform hook code here...
});
```

## PreShoppingCartCheckout

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| cart | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreShoppingCartCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## RunFraudCheck

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | | |
| userid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('RunFraudCheck', 1, function($vars) {
    // Perform hook code here...
});
```

## ShoppingCartCheckoutCompletePage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $smartyvalues | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ShoppingCartCheckoutCompletePage', 1, function($vars) {
    // Perform hook code here...
});
```

## ViewOrderDetailsPage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | | |
| ordernum | | |
| userid | | |
| amount | | |
| paymentmethod | | |
| invoiceid | | |
| status | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ViewOrderDetailsPage', 1, function($vars) {
    // Perform hook code here...
});
```

