+++
next = "/payment-gateways/tokenised-remote-storage"
prev = "/payment-gateways/callbacks"
title = "3D Secure Process"
toc = true
weight = 90

+++

If the merchant gateway supports 3D Secure (also known as Verified by Visa or MasterCard Secure Code), then it can be utilized within WHMCS.

1. Add a function to the module named **yourgatewayname_3dsecure**
2. Return the HTML for the **<form>** post method to take the user to the 3D Secure process.
An example of this is below:

The **_3dsecure** function is passed all the same [variables][variables] that the **_capture** function is.
The return url should be a [callback file][callbacks] to handle the response.

## Example Function

```
<?php
function yourgatewayname_3dsecure(array $params = array()) {
    return '<form method="post" action="https://www.gateway.com/3dsecure/">
<input type="hidden" name="gwlogin" value="' . $params["loginid"] . '" />
<input type="hidden" name="invoiceid" value="' . $params["invoiceid"] . '" />
<input type="hidden" name="amount" value="' . $params["amount"] . '" />
<input type="hidden" name="firstname" value="' . $params["clientdetails"]["firstname"] . '" />
<input type="hidden" name="lastname" value="' . $params["clientdetails"]["lastname"] . '" />
<input type="hidden" name="address" value="' . $params["clientdetails"]["address1"] . '" />
<input type="hidden" name="city" value="' . $params["clientdetails"]["city"] . '" />
<input type="hidden" name="state" value="' . $params["clientdetails"]["state"] . '" />
<input type="hidden" name="postcode" value="' . $params["clientdetails"]["postcode"] . '" />
<input type="hidden" name="country" value="' . $params["clientdetails"]["country"] . '" />
<input type="hidden" name="phonenumber" value="' . $params["clientdetails"]["phonenumber"] . '" />
<input type="hidden" name="email" value="' . $params["clientdetails"]["email"] . '" />
<input type="hidden" name="ccnumber" value="' . $params["cardnum"] . '" />
<input type="hidden" name="expirymonth" value="' . substr($params['cardexp'], 0, 2) . '" />
<input type="hidden" name="expiryyear" value="' . substr($params['cardexp'], 2, 2) . '" />
<input type="hidden" name="cvv2" value="' . $params["cccvv"] . '" />
<input type="hidden" name="return_url" value="' . $params['systemurl'] . '/modules/gateways/callback/yourgatewayname.php" />
<noscript>
<div class="errorbox"><b>JavaScript is currently disabled or is not supported by your
browser.</b><br />Please click the continue button to proceed with the processing of your
transaction.</div>
<p align="center"><input type="submit" value="Continue >>" /></p>
</noscript>
</form>';
}
```

[callbacks]: /payment-gateways/callbacks "Callback Files"
[variables]: /payment-gateways/merchant-gateway#variables "Merchant Gateway Variables"
