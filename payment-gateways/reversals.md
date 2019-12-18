+++
next = "/payment-gateways/3d-secure"
prev = "/payment-gateways/subscription-management"
title = "Payment Reversals"
toc = true
weight = 80

+++

WHMCS 7.2 and later supports payment reversal callbacks.

If your payment gateway provider supports sending notifications when a payment dispute or chargeback is initiated, you can leverage this to have automated actions performed within WHMCS including reverting of next due date increments, changing the invoice status to Collections and sending administrative users an email notification.

## How it works

Supported as part of the callback file, you can trigger a payment reversal action within WHMCS by executing the following function call.

```
/**
 * Reverse a payment.
 *
 * @param string $reverseTransactionId
 * @param string $originalTransactionId
 *
 * @throws Exception
 */
try {
    $reverseTransactionId = '10643229BD2660707';
    $originalTransactionId = '7WA952319L375522P';
    paymentReversed($reverseTransactionId, $originalTransactionId);
} catch (\Exception $e) {
    // Transaction could not be found or already reversed
    $errorMessage = $e->getMessage();
}
```

There are two required input parameters:

* `reverseTransactionId` - The unique transaction ID assigned to the reversal action
* `originalTransactionId` - The unique transaction ID of the original transaction to be reversed

The function will throw exceptions under the following conditions:

* Multiple Original Transaction ID matches found - in the case of more than one transaction being found for a given original Transaction ID, the reversal cannot be processed automatically
* Original Transaction Not Found - occurs when the original Transaction ID is not found in the database
* Transaction Already Reversed - occurs when the original Transaction ID has already been refunded, or the reversal Transaction ID already exists in the database
