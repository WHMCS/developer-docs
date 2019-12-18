 +++
next = "/payment-gateways/installation-activation"
prev = "/payment-gateways/3d-secure"
title = "Tokenised Remote Storage"
toc = true
weight = 100

+++

Tokenisation is the replacement of sensitive payment information with a unique identifier (a token).

Therefore in WHMCS, a tokenised payment gateway module is one where the sensitive payment data is stored remotely by the payment gateway. This reduces the risk of data breaches because it means that unauthorized access to the local system does not risk exposing customer's sensitive payment information.

## Creating a Token Gateway

Payment gateways can operate tokenisation platforms in a variety of ways.

### Capture Token Exchange

At its simplest, a payment gateway may exchange or return a token for you to use for future charges following a regular capture being performed.

For payment gateways that function in this way, you should return the token along with the result from the capture function. WHMCS will then automatically purge the locally stored payment details and replace them with the token.

The following return parameters are supported.

Parameter | Type | Description
---|---|---
status|string|One of either `success`, `pending`, `declined`
declinereason|string|The reason for a decline
transid|string|The Transaction ID returned by the payment gateway
fee|float|The transaction fee returned by the payment gateway
rawdata|string or array|The raw data returned by the payment gateway for logging to the gateway log to aid in debugging
gatewayid|string|The token returned by the payment gateway

#### Example

```
function yourmodulename_capture($params) {
    $gatewayid = $params['gatewayid'];
    $cardnum = $params['cardnum'];
    
    if ($gatewayid) {
        // Make API call to perform capture using the token here
        // Dummy response assumed below in $response variable.        

        return [
            'status' => 'success',
            'transid' => $response['transaction_id']
            // Return a value in gatewayid to update the token only if required
            'gatewayid' => $response['token'],
            'rawdata' => $response,
        ];
    } else {
        // Make API call to perform capture using the card number here
        // Dummy response assumed below in $response variable.
        $response = [];

        return [
            'status' => 'success',
            'transid' => $response['transaction_id']
            'gatewayid' => $response['token'],
            'rawdata' => $response,
        ];
    }
}
```

### Remote Storage

For payment gateways where tokens have to be created and managed separately from capture attempts, you should use the remote storage method within your WHMCS gateway module.

This function will override the default behaviour when entering new, updating an existing, or deleting credit card details.

The following parameters are passed into the `storeremote` function.

Parameter | Type | Description
---|---|---
action|string|One of either `create`, `update`, or `delete`
gatewayid|string|The token for the pay method to be updated
cardtype|string|The card type (Visa, MasterCard, etc..)
cardnum|string|The card number
cardexp|int|The card expiry date (Format: MMYY)
cardstart|int|The card start date (Format: MMYY)
cardissuenum|int|The card issue number

The following return parameters are supported.

Parameter | Type | Description
---|---|---
status|string|One of either `success` or `error`
rawdata|string or array|The raw data returned by the payment gateway for logging to the gateway log to aid in debugging
gatewayid|string|The token returned by the payment gateway

#### Example

```
function yourmodulename_storeremote($params) {
    $action = $params['action'];
    $gatewayid = $params['gatewayid'];
    $cardtype = $params['cardtype'];
    $cardnum = $params['cardnum'];
    $cardexp = $params['cardexp'];
    $cardstart = $params['cardstart'];
    $cardissuenum = $params['cardissuenum'];

    switch ($action) {
        case 'create':
            // Make API call to create a token here
            $postfields = [
                'cardnumber' => $cardnum,
                'cardexpiry' => $cardexp,
                'cardcvv' => $params['cccvv'],
            ];
        
            $ch = curl_init();
            curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/store');
            curl_setopt($ch, CURLOPT_POST, 1);
            curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
            $response = curl_exec($ch);
            curl_close($ch);
        
            $data = json_decode($response);

            return [
                'status' => 'success',
                'gatewayid' => $data->remote_id,
            ];
            break;
        case 'update':
            // Make API call to update a token here
            $postfields = [
                'remote_id' => $gatewayid,
                'cardexpiry' => $cardexp,
            ];
        
            $ch = curl_init();
            curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/update');
            curl_setopt($ch, CURLOPT_POST, 1);
            curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
            $response = curl_exec($ch);
            curl_close($ch);
        
            $data = json_decode($response);
            return [
                'status' => 'success',
                'gatewayid' => $data->remote_id,
            ];
            break;
        case 'delete':
            // Make API call to delete a token here
            $postfields = [
                'remote_id' => $gatewayid,
            ];
        
            $ch = curl_init();
            curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/api/delete');
            curl_setopt($ch, CURLOPT_POST, 1);
            curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
            $response = curl_exec($ch);
            curl_close($ch);
        
            $data = json_decode($response);
            return [
                'status' => 'success',
            ];
            break;
    }
}
```
