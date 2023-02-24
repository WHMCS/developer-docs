+++
title = "Invoices and Quotes"
weight = 10

+++

The following hooks are provided for Invoices and Quotes related events.

## InvoiceCreated

Executed when an invoice has left "Draft" status and is available to its respective client. Execution of this hook occurs after sending the `Invoice Created` email.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string | Indicates where the invoice creation action originated, can be one of `adminarea`, `api` or `autogen` |
| user | mixed | The user who initiated the invoice creation (either `system` or an admin ID value). |
| invoiceid | int | The invoice ID. |
| status | string | The status of the released invoice. |

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

Executes when an invoice is first created. The invoice has not been finalised and delivered to the client at this point. Changes can be made to line items at this point. The invoice totals will be recalculated post execution of this hook point.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string | Indicates where the invoice creation action originated, can be one of `adminarea`, `api` or `autogen` |
| user | mixed | User who initiated the invoice creation, either `system` or an admin ID value |
| invoiceid | int | The ID of the newly created invoice |
| status | string | The status of the newly created invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCreation', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoicePaymentReminder

Executes when an automated invoice payment reminder is sent.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int |  |
| type | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoicePaymentReminder', 1, function($vars) {
    // Perform hook code here...
});
```

## QuoteCreated

Executes when a quote is created.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| quoteid | int |  |
| status | string |  |

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

Executes when a quote status is updated

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| quoteid | int |  |
| status | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('QuoteStatusChange', 1, function($vars) {
    // Perform hook code here...
});
```

