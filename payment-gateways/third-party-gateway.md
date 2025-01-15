+++
next = "/payment-gateways/merchant-gateway"
prev = "/payment-gateways/configuration"
title = "Third Party Gateway"
toc = true
weight = 40

+++

Follow the steps below to create a third party gateway module.

{{% notice info %}}
A Third Party Gateway module is one where a customer leaves the site to pay and returns when the payment process is complete. Examples include PayPal Standard and 2Checkout.
{{% /notice %}}

## Implementation guide

1. Delete the `yourmodulename_capture` function from the module template since this is only required for [Merchant Gateway][merchantgateways] modules.
2. Define and return the HTML code that will forward the user to the payment gateway to complete the payment process inside the `yourmodulename_link` function. This is typically done by way of an HTML form utilizing the **POST** method.
3. Optionally, if your payment gateway supports sending notifications upon successful receipt of payments, create a [Callback File][callbacks] to receive and handle those.
4. If your payment gateway supports refunds, implement support for [Refunds][refunds].

## Variables

The following parameters are passed to the `_link` function along with all [defined configuration parameters][configuration] and their values.

### Invoice Variables
```
$params['invoiceid'] # Invoice ID Number.
$params['description'] # Description (eg. Company Name - Invoice #xxx).
$params['amount'] # Format: xxx.xx
$params['currency'] # Currency Code (eg. GBD, USD, etc.)
```
### Client Variables
```
$params['clientdetails']['firstname'] # Client's First Name.
$params['clientdetails']['lastname'] # Client's Last Name.
$params['clientdetails']['email'] # Client's Email Address.
$params['clientdetails']['address1'] # Client's Address.
$params['clientdetails']['address2']
$params['clientdetails']['city']
$params['clientdetails']['state']
$params['clientdetails']['postcode']
$params['clientdetails']['country']
$params['clientdetails']['model'] # An instance of WHMCS\User\Client. See below.
$params['clientdetails']['phonenumber']
```

For more information on the `model` variable, see our <a href="https://classdocs.whmcs.com/">Class Documentation</a>.

### System Variables
```
$params['companyname'] # Your Company Name setting in WHMCS.
$params['systemurl'] # The URL to the WHMCS Client Area.
$params['returnurl'] # The return URL for the invoice.
$params['langpaynow'] # The language string for "Pay Now".
$params['name'] # Module display name.
$params['paymentmethod'] # Module name.
$params['whmcsVersion'] # WHMCS Version Number.
```

## Response Format

The `_link` function should return an HTML code block that can be rendered to the user. This should typically take the format of an HTML form.

## Simple Example

Below is a very simple demonstration of a link function that forwards the end user to `https://www.example.com/checkout` using a form post containing the invoice data. For a more complete example, please refer to the [Sample Third Party Gateway module on GitHub][githubsample].

```
function yourmodulename_link($params) {
    return '<form method="post" action="https://www.example.com/checkout">
        <input type="invoice_number" value="' . $params['invoiceid'] . '" />
        <input type="description" value="' . $params['description'] . '" />
        <input type="amount" value="' . $params['amount'] . '" />
        <input type="currency" value="' . $params['currency'] . '" />
        <input type="submit" value="' . $params['langpaynow'] . '" />
        </form>';
}
```

[configuration]: /payment-gateways/configuration "Configuration Parameters"
[merchantgateways]: /payment-gateways/merchant-gateway "Merchant Gateways"
[githubsample]: https://github.com/WHMCS/sample-gateway-module "Sample Third Party Gateway module on GitHub"
[callbacks]: /payment-gateways/callbacks "Callback Files"
[refunds]: /payment-gateways/refunds "Refunding Transactions"
