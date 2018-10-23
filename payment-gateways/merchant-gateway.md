+++
next = "/payment-gateways/callbacks"
prev = "/payment-gateways/third-party-gateway"
title = "Merchant Gateway"
toc = true
weight = 30

+++

Follow the steps below to create a third party gateway module.

{{% notice info %}}
A Merchant Gateway is one where a customer enters credit card details in WHMCS. The payment processes in the background. Can also include 3D Secure where the user leaves your site. Examples include PayPal Pro, Authorize.net AIM
{{% /notice %}}

## Implementation guide

1. Delete the `yourmodulename_link` function from the module template since this is only required for [Third Party Gateway][thirdparty] modules.
2. Enter the gateway-specific code for processing the payment capture into the `yourmodulename_capture` function. Typically this takes the format of an HTTP/Curl request to the gateway provider's API.
3. If the gateway supports 3D Secure (Verified by Visa or MasterCard Secure Code) then please refer to [3D Secure][3d-secure].
4. If your payment gateway supports refunds, implement support for [Refunds][refunds].

## Variables

The following parameters are passed to the `_capture` function along with all [defined configuration parameters][configuration] and their values.

### Invoice Variables
```
$params['invoiceid'] # Invoice ID Number
$params['description'] # Description (eg. Company Name - Invoice #xxx)
$params['amount'] # Format: xxx.xx
$params['currency'] # Currency Code (eg. GBD, USD, etc...)
```

### Card Details
```
$params['cardtype'] # the Card Type (Visa, MasterCard, etc…)
$params['cardnum'] # the Card Number
$params['cardexp'] # the Card’s Expiry Date (Format: MMYY)
$params['cardstart'] # the Card’s Start Date (Format: MMYY)
$params['cardissuenum'] # the Card’s Issue Number (Switch/Solo Cards)
$params['cccvv'] # Not always present (recurring transactions)
# but would always be present for client initiated attempts
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
```

## Response Format

The capture function should always return an array containing information about the transaction attempt.  This should take the following format:

```
return array(
    'status' => 'success',
    'rawdata' => $responseData,
    'transid' => $transactionId,
    'fee' => $feeAmount,
);
```

For a successful capture, the status should be returned as the string `success`.  For anything else, return a status that indicates the reason for failure.  Common failure response status values include `declined` and `error`.

The raw data you return will be recorded to the gateway log to aide in debugging. It can accept either a string or array.

## Simple Example

Below is a very simple demonstration of a capture function that submits a payment capture request and receives a JSON response. For a more complete example, please refer to the [Sample Merchant Gateway module on Github][githubsample].

```
function yourmodulename_capture($params) {

    $postfields = [
        'invoiceid' => $params['invoiceid'],
        'amount' => $params['amount'],
        'currency' => $params['currency'],
        'cardnumber' => $params['cardnum'],
        'cardexpiry' => $params['cardexp'],
        'cardcvv' => $params['cccvv'],
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/capture');
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    $data = json_docode($response);

    return array(
        'status' => ($data->success == 1) ? 'success' : 'declined',
        'rawdata' => $data,
        'transid' => $data->transaction_id,
        'fee' => $data->fees,
    );
}
```

[configuration]: /payment-gateways/configuration "Configuration Parameters"
[thirdparty]: /payment-gateways/third-party-gateways "Third Party Gateways"
[githubsample]: https://github.com/WHMCS/sample-merchant-gateway "Sample Merchant Gateway module on Github"
[refunds]: /payment-gateways/refunds "Refunding Transactions"
[3d-secure]: /provisioning-modules/3d-secure "3D Secure Process"
