+++
next = "/payment-gateways/refunds"
prev = "/payment-gateways/merchant-gateway"
title = "Callback Files"
toc = true
weight = 40

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

This function can be used to retrieve the configuration data for a module as specified in the **_config** array.
For example, it might be needed to get a gateway username or secret key to validate a callback.

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

Use this function to verify that the invoice ID received in a callback is valid.
Pass the $invoiceid and the gateway name into the function.
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

Use this function to check for any existing transactions for a given transaction ID.
This protects against duplicate callbacks for the same transaction.
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
The first input parameter should be the name of the gateway module.
The second input parameter should be an array of data received, such as the **$_POST** or **$_REQUEST** super globals.
The last input parameter should be the human readable result/status to display in the log.
