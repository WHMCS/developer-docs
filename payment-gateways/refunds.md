+++
next = "/payment-gateways/subscription-management"
prev = "/payment-gateways/callbacks"
title = "Refunds"
toc = true
weight = 70

+++

This function will be called any time a transaction is requested to be refunded from within WHMCS.

It is supported by all payment gateway module types.  If your payment gateway module does not support refunds, simply do not define this function within your module.

Like with a capture attempt, upon completion of the refund, you are expected to return an array containing the transaction details consisting of the status, and if successful a transaction ID and optionally some data to be recorded to the gateway log for debugging purposes.

## Variables

The following parameters are made available in the parameters passed to the refund function.

### Invoice Variables
```
$params['invoiceid'] # Invoice ID Number
$params['transid'] # Transaction ID to be refunded
$params['amount'] # Amount to be refunded (Format: xxx.xx)
$params['currency'] # Currency Code (eg. GBD, USD, etc...)
```
### Client Variables
```
$params['clientdetails']['firstname'] # Client's First Name
$params['clientdetails']['lastname'] # Client's Last Name
$params['clientdetails']['email'] # Client's Email Address
$params['clientdetails']['address1'] # Client's Address
$params['clientdetails']['address2']
$params['clientdetails']['city']
$params['clientdetails']['state']
$params['clientdetails']['postcode']
$params['clientdetails']['country']
$params['clientdetails']['phonenumber']
```

### System Variables
```
$params['companyname'] # your Company Name setting in WHMCS
$params['systemurl'] # the url to the Client Area
$params['name'] # Module Display Name
$params['moduleName'] # Module System Name
```

## Response Format

Upon completion of the refund attempt, return the results in the following format:

```
return array(
    'status' => 'success',
    'rawdata' => $responseData,
    'transid' => $refundTransactionId,
    'fees' => $feeAmount,
);
```

* **status** - `success` if successful, otherwise `declined` or `error`
* **rawdata** - data to be recorded in the gateway log for debugging purposes
* **transid** - Unique Transaction ID for the refund transaction
* **fees** - Optional fee amount for the fee value refunded
