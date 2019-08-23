 +++
next = "/payment-gateways/installation-activation"
prev = "/payment-gateways/tokenised-remote-storage"
title = "Remote Input Token Storage"
toc = true
weight = 110

+++

Remote input gateways provide a way for a payment details to be entered using third party interfaces, but without a client leaving the WHMCS install.

This is commonly done using a posted form to an iFrame result.

## Creating a Remote Input Gateway

A remote input gateway requires two functions to be implemented in addition to the standard `capture`.
These functions are `remoteinput` and `remoteupdate`.

Once processed, a notification will be sent to a [callback file][callbacks] where the Pay Method should be stored and the payment applied.

For a more complete example, please refer to the [Sample Remote Input Gateway module on Github][github-sample].

## Remote Input

The `remoteinput` function will run when adding a new payment method as part of checkout, or when adding a new payment method outside of the checkout process.

Return the HTML form that should be output to the page, an array is not supported.
The form will be automatically submitted into an iFrame.

### Example

```
function yourmodulename_remoteinput($params)
{
    $code='<form method="post" action="https://www.example.com/remote/input">
    <input type="hidden" name="api_user" value="' . $params["api_user"] . '" />
    <input type="hidden" name="api_secret" value="' . $params["api_secret"] . '" />
    <input type="hidden" name="amount" value="' . $params["amount"] . '" />
    <input type="hidden" name="invoice_id" value="' . $params["invoiceid"] . '" />
    <input type="hidden" name="firstname" value="' . $params["clientdetails"]["firstname"] . '" />
    <input type="hidden" name="lastname" value="' . $params["clientdetails"]["lastname"] . '" />
    <input type="hidden" name="address1" value="' . $params["clientdetails"]["address1"] . '" />
    <input type="hidden" name="city" value="' . $params["clientdetails"]["city"] . '" />
    <input type="hidden" name="state" value="' . $params["clientdetails"]["state"] . '" />
    <input type="hidden" name="postcode" value="' . $params["clientdetails"]["postcode"] . '" />
    <input type="hidden" name="country" value="' . $params["clientdetails"]["country"] . '" />
    <input type="hidden" name="phonenumber" value="' . $params["clientdetails"]["phonenumber"] . '" />
    <input type="hidden" name="email" value="' . $params["clientdetails"]["email"] . '" />
    <input type="hidden" name="SaveCard" value="Y" />
    <input type="hidden" name="cust_id" value="' . $params["clientdetails"]["id"] . '" />
    <input type="hidden" name="trans_method" value="CC" />
    <input type="hidden" name="post_return_url_approved" value="' . $params['systemurl'] . 'modules/gateways/callback/yourmodulename.php" />
    <input type="hidden" name="post_return_url_declined" value="' . $params['systemurl'] . 'modules/gateways/callback/yourmodulename.php" />
    <noscript>
    <input type="submit" value="Click here to continue &raquo;" />
    </noscript>
    </form>';

    return $code;
}
```

## Remote Update

The `remoteupdate` function will run when updating a payment method.

Return the HTML required for updating the payment method. This example uses 

### Example

```
function yourmodulename_remoteupdate($params)
{
    $gatewayId = $params['gatewayid'];
    if (!$gatewayId) {
        return '<div class="alert alert-info">You must pay your first invoice before you can update your stored details here.</p>';
    }

    $requestParams = [
        'token' => $params['gatewayid'],
        'api_user' => $params['api_user'],
        'api_secret' => $params['api_secret'],
    ];

    $request = http_build_query($requestParams);
    
    return '<iframe src="https://www.example.com/remote/update?' . $request . '"></iframe>';
}
```

[callbacks]: /payment-gateways/callbacks "Callback Files"
[github-sample]: https://github.com/WHMCS/sample-remote-input-gateway "Sample Remote Input Gateway module on Github"
