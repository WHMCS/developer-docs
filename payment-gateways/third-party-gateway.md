+++
next = "/gateway-modules/merchant-gateway"
prev = "/gateway-modules/getting-started"
title = "Third Party Gateway"
toc = true
weight = 20

+++

Follow the steps below to create a third party gateway module.
A module where the customer leaves WHMCS to make the payment.
Delete the _capture function before activating the new gateway module in WHMCS.

1. Delete the **_capture** function from the module template.
2. Enter the gateway-specific code for taking the user to the payment process within the _link function.
An example of this step is in the gateway module template supplied with the dev kit.
The code output by this function is HTML, usually for a <**form**> with a post method.

## Variables <a id="variables"></a>

### Invoice Variables <a id="invoice-variables"></a>
```
$params['invoiceid'] # Invoice ID Number
$params['description'] # Description (eg. Company Name - Invoice #xxx)
$params['amount'] # Format: xxx.xx
$params['currency'] # Currency Code (eg. GBD, USD, etc...)
```
### Client Variables <a id="client-variables"></a>
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

### System Variables <a id="system-variables"></a>
```
$params['companyname'] # your Company Name setting in WHMCS
$params['systemurl'] # the url to the Client Area
```

## Additional Information <a id="additional-information"></a>

1. Processing of a payment is in a callback file separate from the module.
(see [here][callbacks] for more information).

2. If the gateway won't support automated refunds, delete the _refund function.
Otherwise, refer to the Refund section on page 7 of the sample module.

[callbacks]: /gateway-modules/callbacks "Callback Files"
