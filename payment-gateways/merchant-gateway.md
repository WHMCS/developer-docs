+++
next = "/payment-gateways/callbacks"
prev = "/payment-gateways/third-party-gateway"
title = "Merchant Gateway"
toc = true
weight = 30

+++

A merchant gateway is where the customer enters their card details via the client area.
To create one: Delete the _link function before activating the new module in WHMCS.

1. Delete the _link function from the module template.
2. Enter the gateway-specific code for processing the payment into the _capture function.
Generally, this takes the format of an HTTP/Curl request to the gateway provider's API.

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

### Card Details <a id="card-details"></a>
```
$params['cardtype'] # the Card Type (Visa, MasterCard, etc…)
$params['cardnum'] # the Card Number
$params['cardexp'] # the Card’s Expiry Date (Format: MMYY)
$params['cardstart'] # the Card’s Start Date (Format: MMYY)
$params['cardissuenum'] # the Card’s Issue Number (Switch/Solo Cards)
$params['cccvv'] # Not always present (recurring transactions)
# but would always be present for client initiated attempts
```

## Responses <a id="responses"></a>

### Success

Once processed, and the transaction has a response, return an array with the results to WHMCS.
For a successful capture, use the following format:

```
return array(
    "status" => "success", # The status index must be success to tell WHMCS that the capture was successful.
    "transid" => $results["transid"], # The transid key should be the value of the transaction ID that came back from the gateway.
    "rawdata" => $results, # The rawdata key should be an array of the data returned from the gateway for storage in the WHMCS Gateway Log.
);
```

### Failure


If the transaction were to fail, use the following format:

```
return array(
    "status" => "declined",
    "rawdata" => $results,
);
```

The status key can be any value (declined, error, invalid hash, etc).
This value will display as the reason for failure, in the gateway log.
The rawdata key should be an array of the data returned from the gateway for storage in the WHMCS Gateway Log.

If the gateway supports 3D Secure (Verified by Visa or MasterCard Secure Code) then please refer [here][3d-secure].

## Refunds <a id="refunds"></a>

Code for processing a refund goes into the **_refund** function.
This receives the same variables as the **_capture** function, but with an added transaction id:

```
$params['transid'] # the transaction ID of the original transaction to refund
```

The return arrays for a success or failure should be exactly the same as described above for the **_capture** function.
If the gateway module will not support refunds, delete the **_refund** function from the module file.

[3d-secure]: /provisioning-modules/3d-secure "3D Secure Process"
