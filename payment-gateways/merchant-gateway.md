+++
next = "/payment-gateways/displaying-balances"
prev = "/payment-gateways/third-party-gateway"
title = "Merchant Gateway"
toc = true
weight = 50

+++

Follow the steps below to create a third party gateway module.

{{% notice info %}}
A Merchant Gateway is one where a customer enters credit card details in WHMCS. The payment processes in the background. This can also include 3D Secure when the user leaves your site. Examples include PayPal Pro, Authorize.net, and AIM.
{{% /notice %}}

## Implementation guide

1. Delete the `yourmodulename_link` function from the module template since this is only required for [Third Party Gateway][thirdparty] modules.
2. Enter the gateway-specific code for processing the payment capture into the `yourmodulename_capture` function. Typically, this takes the format of an HTTP/Curl request to the gateway provider's API.
3. If the gateway supports 3D Secure (Verified by Visa or MasterCard Secure Code) refer to [3D Secure][3d-secure].
4. If your payment gateway supports refunds, implement support for [Refunds][refunds].

## Variables

The following parameters are passed to the `_capture` function along with all [defined configuration parameters][configuration] and their values.

Parameter | Type | Description
---|---|---
invoiceid|integer|Invoice ID number.
description|string|Description (for example, `Company Name - Invoice #xxx`).
amount|float|Format: `xxx.xx`
currency|string|Currency code (for example, GBP or USD).
cardtype|string|The card type (for example, Visa or MasterCard).
cardnum|string|The card number.
cardexp|string|The card expiry date (format: MMYY).
cardstart|string|The card start date (format: MMYY).
cardissuenum|string|The card issue number.
cccvv|string|Only available for card holder present initiated payment attempts.
clientdetails|array|An array of client details that includes the following indices: firstname, lastname, email, address1, address2, city, state, postcode, country (ISO code), model (an instance of `<a href="https://classdocs.whmcs.com/">WHMCS/User/Client</a>`), and phonenumber.
companyname|string|The *Company Name* setting in WHMCS.
systemurl|string|The URL to the client area of the WHMCS installation.

## Response

The following return parameters are supported.

Parameter | Type | Description
---|---|---
status|string|One of either `success`, `pending`, or `declined`.
declinereason|string|The reason why a transaction was declined.
transid|string|The Transaction ID returned by the payment gateway.
fee|float|(Optional) The transaction fee returned by the payment gateway.
rawdata|string or array|The raw data returned by the payment gateway for logging to the gateway log to aid in debugging.
gatewayid|string|See [Tokenised Remote Storage][tokenised-remote-storage].

### Example Return

The capture function should always return an array containing information about the transaction attempt. This should take the following format:

```
return array(
    'status' => 'success',
    'rawdata' => $responseData,
    'transid' => $transactionId,
    'fee' => $feeAmount,
);
```

For a successful capture, the status should be returned as the string `success`.

For payments that are pending and do not require an immediate payment in WHMCS, the status should be `pending`.

For anything else, return a status that indicates the reason for failure. Common failure response status values include `declined` and `error`.

The raw data you return will be recorded to the gateway log to aid in debugging. It can accept either a string or an array.

## Simple Example

Below is a demonstration of a capture function that submits a payment capture request and receives a JSON response. For a more complete example, please refer to the [Sample Merchant Gateway module on GitHub][githubsample].

```
function yourmodulename_capture($params) {

    $postfields = [
        'invoiceid' => $params['invoiceid'],
        'amount' => $params['amount'],
        'currency' => $params['currency'],
        'cardnumber' => $params['cardnum'],
        'cardexpiry' => $params['cardexp'],
        'cardcvv' => $params['cccvv'],
        'card_holder_name' => $params['clientdetails']['firstname']
            . ' - ' . $params['clientdetails']['lastname'],
        'card_address' => [
            'address_line_1' => $params['clientdetails']['address1'],
            'city' => $params['clientdetails']['city'],
            'state' => $params['clientdetails']['state'],
            'postcode' => $params['clientdetails']['postcode'],
            'country' => $params['clientdetails']['country'],
        ],
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/capture');
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    $data = json_decode($response);

    if ($data->success == 1) {
        $return = [
            'status' => 'success',
            'transid' => $data->transaction_id,
            'fee' => $data->fee,
            'rawdata' => $data,
        ];
    } else {
        $return = [
            'status' => 'declined',
            'declinereason' => $data->decline_reason,
            'rawdata' => $data,
        ];
    }
    return $return;
}
```

[configuration]: /payment-gateways/configuration "Configuration Parameters"
[thirdparty]: /payment-gateways/third-party-gateway "Third Party Gateways"
[githubsample]: https://github.com/WHMCS/sample-merchant-gateway "Sample Merchant Gateway module on GitHub"
[refunds]: /payment-gateways/refunds "Refunding Transactions"
[3d-secure]: /payment-gateways/3d-secure "3D Secure Process"
[tokenised-remote-storage]: /payment-gateways/tokenised-remote-storage "Tokenised Remote Storage"
