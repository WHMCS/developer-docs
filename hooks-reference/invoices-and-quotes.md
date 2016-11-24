+++
title = "Invoices and Quotes"
weight = 10

+++

The following hooks are provided for Invoices and Quotes related events.

## AddInvoiceLateFee

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddInvoiceLateFee', 1, function($vars) {
    // Perform hook code here...
});
```

## AddInvoicePayment

Invoked when a payment is applied to an invoice (including partial payments).

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int | The invoice id payment was applied to |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddInvoicePayment', 1, function($vars) {
    // Perform hook code here...
});
```

## AddTransaction

Executes when a transaction is created. Can be a payment or a refund.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | Transaction ID |
| userid | int | User ID |
| currency | int | Currency ID (if not related to a client, otherwise client currency) |
| gateway | string |  |
| date | \datetime |  |
| description | string |  |
| amountin | float |  |
| fees | float |  |
| amountout | float |  |
| rate | float | Exchange rate |
| transid | string | Transaction ID provided by gateway or admin user |
| invocieid | int | Invoice ID to which the transaction was applied |
| refundid | int | Refund ID if a refund |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddTransaction', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminAreaViewQuotePage

Run this hook before we create the quote below. This has been done to keep the original hook running order.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminAreaViewQuotePage', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterInvoicingGenerateInvoiceItems

Executes after invoice generation allowing for after invoicing clean-up.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterInvoicingGenerateInvoiceItems', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceCancelled

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCancelled', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceChangeGateway

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | | |
| paymentmethod | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceChangeGateway', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceCreated

Executes when an invoice is created following sending the Invoice Created email.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string |  |
| user | string|int | System or Admin User |
| invoiceid | int | The invoice ID that was created |
| status | string | The status of the new invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCreated', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceCreation

Executes when an invoice is first created. The invoice has not been delivered to the client at this point.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string |  |
| user | string|int | System or Admin User |
| invoiceid | int | The invoice ID that was created |
| status | string | The status of the new invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCreation', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceCreationAdminArea

Executes when an invoice is first created by an admin user. The invoice has not been delivered to the client at this point.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string |  |
| user | string|int | System or Admin User |
| invoiceid | int | The invoice ID that was created |
| status | string | The status of the new invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCreationAdminArea', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceCreationPreEmail

Executes when an invoice is created immediately prior to sending the Invoice Created email.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string |  |
| user | string|int | System or Admin User |
| invoiceid | int | The invoice ID that was created |
| status | string | The status of the new invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCreationPreEmail', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoicePaid

Executes when an invoice is Paid following the email receipt having been sent and any automation tasks associated with the payment action having been run.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoicePaid', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoicePaidPreEmail

Executes when an invoice is Paid prior to any email or automation tasks associated with the payment action having been run.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoicePaidPreEmail', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceRefunded

Executes when an invoice status is changed to Refunded.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int | Invoice ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceRefunded', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceSplit

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| originalinvoiceid | | |
| newinvoiceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceSplit', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceUnpaid

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceUnpaid', 1, function($vars) {
    // Perform hook code here...
});
```

## LogTransaction

Runs any time a payment gateway callback is received and logged.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| gateway | string | The payment gateway name |
| data | string | A string formatted version of all post data received |
| result | string | The status the gateway module returned |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LogTransaction', 1, function($vars) {
    // Perform hook code here...
});
```

## ManualRefund

Executes when an invoice is refunded via the Manual Refund option.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| transid | string | Transaction ID of the original payment |
| amount | float | The amount to be refunded |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ManualRefund', 1, function($vars) {
    // Perform hook code here...
});
```

## PreInvoicingGenerateInvoiceItems

Executes prior to invoice generation allowing for manipulation of items prior to invoice generation.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreInvoicingGenerateInvoiceItems', 1, function($vars) {
    // Perform hook code here...
});
```

## QuoteCreated

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| quoteid | | |
| status | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('QuoteCreated', 1, function($vars) {
    // Perform hook code here...
});
```

## QuoteStatusChange

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| quoteid | | |
| status | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('QuoteStatusChange', 1, function($vars) {
    // Perform hook code here...
});
```

## UpdateInvoiceTotal

Executes when an invoice is updated with changes to or additions of line items. Can be used to manipulate the invoice.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int | Invoice ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('UpdateInvoiceTotal', 1, function($vars) {
    // Perform hook code here...
});
```

## ViewInvoiceDetailsPage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ViewInvoiceDetailsPage', 1, function($vars) {
    // Perform hook code here...
});
```

## acceptQuote

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| quoteid | | |
| invoiceid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('acceptQuote', 1, function($vars) {
    // Perform hook code here...
});
```

