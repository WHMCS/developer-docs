+++
next = "/payment-gateways/refunds"
prev = "/payment-gateways/transaction-information"
title = "Callback Files"
toc = true
weight = 60

+++

If you are building a payment gateway that supports notifying you when a payment is successful you should create a callback file as part of your module to receive and handle those notifications.

A callback file should process and validate the notification and then call one of several functions made available by WHMCS to log and apply the payment.

## Creating a callback file

A sample callback file is included in the sample gateway module named `callback/gatewaymodule.php`.

We recommend using the sample file as a starting point for your creating your own gateway callback file. Rename it to match the name of your own gateway module.

Most callback files should use the following workflow:

1. Implement logic to validate the authenticity of the payment gateway callback and prevent abuse.
2. Validate the invoice ID the callback relates to using the `checkCbInvoiceID` helper method.
3. Verify the transaction ID has not already been recorded using the `checkCbTransID` helper method.
4. Log the transaction to the WHMCS Gateway Log using the `logTransaction` helper method.
5. Apply the payment to the invoice using the `addInvoicePayment` helper method.

## Callback Redirection

When a payment is received, a payment notification containing the transaction details may be sent to the gateway module's callback file. The URL of the callback file would be considered the `Callback URL` (e.g. https://example.com/whmcs/modules/gateways/callback/gatewaymodule.php).

Some gateways allow you to pass a `Return URL` and a `Callback URL` in the payment button code. WHMCS can provide the `Return URL` during the initial payment submission to the gateway via the `$params['returnurl']` parameter, which is made available in the gateway module `_link` function.

Other payment gateways require the `Return URL` to be specified in the payment gateway's control panel settings outside of WHMCS to return the client upon completion of a payment (e.g. a success/failure page or redirect to the paid invoice). Create the file for this page as required and place it at `/modules/gateways/yourgatewayname/`.
The URL to this page will be considered the `Return URL` (e.g. https://example.com/whmcs/modules/gateways/yourgatewayname/customfile.php).

This URL could then be specified in the payment gateway's control panel settings outside of WHMCS, leaving just the notification URL specified in the gateway module's `_link` function.

If the gateway only supports one URL for both payment notification and redirection after payment, visitors can be redirected to the callback file and output provided to return them to the Client Area via a link or meta refresh. This output should be provided by the callback file after the `addInvoicePayment` and `logTransaction` functions.

## Helper Functions

The following helper functions are made available for use in payment gateway callback files.

### Get Gateway Variables

```
/**
 * Get Gateway Variables.
 *
 * Retrieves configuration setting values for a given module name.
 *
 * @param string $gatewayName
 */
$gatewayParams = getGatewayVariables('yourgatewayname');
```

This function can be used to retrieve the configuration data for a module as specified in the `_config` array. For example, it might be needed to get a gateway username or secret key to validate a callback.

### Validate Callback Invoice ID

```
/**
 * Validate Callback Invoice ID.
 *
 * Checks invoice ID is a valid invoice number. Note it will count an
 * invoice in any status as valid.
 *
 * Performs a die upon encountering an invalid Invoice ID.
 *
 * Returns a normalised invoice ID.
 *
 * @param int $invoiceId
 * @param string $gatewayName
 */
$invoiceId = checkCbInvoiceID($invoiceId, $gatewayName);
```

Use this function to verify that the invoice ID received in a callback is valid. Pass the `$invoiceid` and the gateway name into the function.

If the invoice number is invalid, the callback script execution will be halted.

### Validate Callback Transaction ID

```
/**
 * Check Callback Transaction ID.
 *
 * Performs a check for any existing transactions with the same given
 * transaction number.
 *
 * Performs a die upon encountering a duplicate.

 * @param string $transactionId
 */
checkCbTransID($transactionId);
```

Use this function to check for any existing transactions for a given transaction ID. This protects against duplicate callbacks for the same transaction.

If the transaction ID is already in the database, the callback script execution will be halted.

### Log Transaction

```
/**
 * Log Transaction.
 *
 * Add an entry to the Gateway Log for debugging purposes.
 *
 * The debug data can be a string or an array.
 *
 * @param string $gatewayName Display label
 * @param string|array $debugData Data to log
 * @param string $transactionStatus Status
 */
logTransaction($gatewayName, $_POST, $transactionStatus);
```

Use this function to create a gateway log entry.

* The first input parameter should be the name of the gateway module.
* The second input parameter should be an array of data received (for example, the `$_POST` or `$_REQUEST` super globals).
* The last input parameter should be the human readable result or status to display in the log.

### Add Payment to the Invoice

```
/**
 * Add Invoice Payment.
 *
 * Apply a payment to the given invoice ID.
 *
 * @param int $invoiceId         Invoice ID
 * @param string $transactionId  Transaction ID
 * @param float $paymentAmount   Amount paid (defaults to full balance)
 * @param float $paymentFee      Payment fee (optional)
 * @param string $gatewayModule  Gateway module name
 */
addInvoicePayment(
    $invoiceId,
    $transactionId,
    $paymentAmount,
    $paymentFee,
    $gatewayModuleName
);
```

Use this function to apply the payment to an invoice.

* The first parameter should be the invoice ID to apply the payment to.
* The second parameter should be the unique transaction ID provided by the payment gateway.
* The third parameter should be the amount to be credited to the invoice. If this value is `0` or an empty string, the payment will be assumed to be the full balance due for the invoice.
* The fourth parameter should be the fee charged by the gateway. If this is unavailable, set this to `0.00`.
* The fifth parameter should be your gateway module name. You can use `$gatewayParams['paymentmethod']` for this.

This documentation assumes you are following the sample callback file in the sample module which defines this variable and populates it with the gateway parameters from WHMCS.
