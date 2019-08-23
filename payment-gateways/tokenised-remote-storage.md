 +++
next = "/payment-gateways/remote-input-gateway"
prev = "/payment-gateways/3d-secure"
title = "Tokenised Remote Storage"
toc = true
weight = 100

+++

With increasing rules & requirements surrounding the storing of credit card details,
merchant gateways are offering services where repeat rebills can be performed without needing to store credit card details.
Gateway modules can use this functionality.

The basic logic behind token gateways in WHMCS is that clients must either have a credit card number or a token stored in order for recurring billing.
Add a function named **_storeremote** to the custom gateway module.
This function will override the default storage when entering new credit card details.
Instead of saving in the database, **_storeremote** communicates with the gateways API, and returns a token that gets assigned to WHMCS.

## Variables

A number of variables as passed into the **_storeremote** function as follows.

```
$params['gatewayid'] # the token stored for the client
$params['cardtype'] #the Card Type (Visa, MasterCard, etc…)
$params['cardnum'] # the Card Number
$params['cardexp'] # the Card’s Expiry Date (Format: MMYY)
$params['cardstart'] # the Card’s Start Date (Format: MMYY)
$params['cardissuenum'] # the Card’s Issue Number (Switch/Solo Cards)
```

## Calling

On the first call, the gatewayid will be empty.
When empty, create a new profile at the gateway.
On later calls, the created gatewayid that will be passed in and the existing profile updated.
If the cardnum variable is empty, this indicates a removal request of the stored credit card details.
Once the card details have been updated or stored remotely, return either a success or failure response to tell WHMCS if it worked.
If successful, return also the token that has been assigned:

```
return array(
    "status" => "success",
    "gatewayid" => $results["token"],
    "rawdata" => $results,
);

return array(
    "status" => "failed",
    "rawdata" => $results,
);
```

When this function exists in a gateway module, WHMCS will only store the card type, expiry date and the last 4 digits locally in the database.
Clients and Admins will still be able to see exactly what card is stored remotely from within WHMCS.
Then within the capture function, instead of `$params[‘cardnum’]`, `$params[‘gatewayid’]` is received to perform the capture.
