+++
title = "Shopping Cart"
weight = 10

+++

The following hooks are provided for Shopping Cart related events.

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

