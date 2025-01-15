 +++
next = "/payment-gateways/installation-activation"
prev = "/payment-gateways/tokenised-remote-storage"
title = "Remote Input Token Storage"
toc = true
weight = 110

+++

A remote input module is a type of merchant gateway that accepts input of pay
method data remotely within an iFrame so that it appears transparent to the end
user, and then exchanges it for a token that is returned to WHMCS to be stored for future billing attempts.

Within WHMCS, sensitive payment data such as a card number or bank account information is not stored
locally when a remote input module is used.

## Creating a Remote Input Gateway

A remote input gateway requires two functions to be implemented in addition to the standard `capture`.
These functions are `remoteinput` and `remoteupdate`.

Once processed, a notification will be sent to a [callback file][callbacks] where the Pay Method should be stored and the payment applied.

For a more complete example, please refer to the [Sample Remote Input Gateway module][github-sample] or [Sample Remote Input Bank Gateway module on GitHub][github-bank-sample].

## Remote Input

The `remoteinput` function will be called when adding a new payment method as part of checkout,
or when adding a new payment method outside of the checkout process.

The remote input function is required to return an HTML form that will be automatically submitted into an iframe target.
The page rendered within the iframe should allow the user to enter card or bank details in one of 2 workflow scenarios:

* Making payment using a new card or bank - in this workflow the remote endpoint should allow the user to enter card/bank details, generate a token, and capture payment for the requested amount
* Adding a new card or bank to the users account - in this workflow the remote endpoint should allow the user to enter card/bank details and generate a token, but not perform any immediate capture

The workflow type can be determined based on if an invoiceid and amount parameter is received as part of the parameters passed to the `remoteinput` function.

### Example

```
function yourmodulename_remoteinput($params)
{
    return '<form method="post" action="https://www.example.com/remote/input">
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
    <input type="hidden" name="cust_id" value="' . $params["clientdetails"]["id"] . '" />
    <input type="hidden" name="return_url" value="' . $params['systemurl'] . 'modules/gateways/callback/yourmodulename.php" />
    <noscript>
        <input type="submit" value="Click here to continue &raquo;" />
    </noscript>
</form>';
}
```

## Remote Update

The `remoteupdate` function will be called when a pay method is requested to be modified and should allow the user to edit the data of on an existing token.

The expected return of this function is direct HTML output. It provides
more flexibility than the remote input function by not restricting the
return to a form that is posted into an iframe. We still recommend using
an iframe where possible, but the update can sometimes be handled by
way of a modal, popup or other such facility.

### Example

```
function yourmodulename_remoteupdate($params)
{
    $formAction = 'https://www.example.com/remote/update';
    $formFields = [
        'api_user' => $params['api_user'],
        'api_secret' => $params['api_secret'],
        'token' => $params['gatewayid'],
        'custom_reference' => $params['paymethodid'],
    ];

    $formOutput = '';
    foreach ($formFields as $key => $value) {
        $formOutput .= '<input type="hidden" name="' . $key . '" value="' . $value . '">' . PHP_EOL;
    }
    
    return '<div id="frmRemoteCardProcess" class="text-center">
    <form method="post" action="' . $formAction . '" target="remoteUpdateIFrame">
        ' . $formOutput . '
        <noscript>
            <input type="submit" value="Click here to continue &raquo;">
        </noscript>
    </form>
    <iframe name="remoteUpdateIFrame" class="auth3d-area" width="90%" height="600" scrolling="auto" src="http://about:blank"></iframe>
</div>
<script>
    setTimeout("autoSubmitFormByContainer(\'frmRemoteCardProcess\')", 1000);
</script>';
}
```

### Disallowing Remote Update Example

In some circumstances, it may be appropriate to disallow remote updates for Pay Methods.

To achieve this, you can return an alert to be displayed in place of a form:
```
function yourmodulename_remoteupdate($params)
{
    return <<<HTML
<div class="alert alert-info text-center">
    Updating your card/bank is not possible. Please create a new Pay Method to make changes.
</div>
HTML;
}
```

## Helper Functions

The following functions are available in WHMCS 7.9 and later. We recommend using these functions
within the callback handler of a remote input gateway to create a new pay method or update an existing one.
Both functions return a boolean `true` on a success, and any error will throw an exception that
should be caught and logged.

### createCardPayMethod

This function can be used to add a new card pay method to a client account.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientId | int | The ID of the client for the new pay method |
| gatewayName | string | The name of the module adding the pay method |
| cardNumber | string | The card number (or last 4 digits). Full card number will not be stored for remote pay methods |
| cardExpiryDate | string | Card expiry date in mmyy format |
| cardType | null or string | The card type to use. Null will attempt to get card type from card number |
| cardStartDate | null or string | Optional. Card start date in mmyy format |
| cardIssueNumber | null or string | Optional. The issue number for the card |
| remoteToken | string | Required for a remote pay method. The remote token for a remote pay method.
| billingContactId | string or integer | Optional. The ID of the billing contact to use. Defaults to 'billing' |
| description | string | The description for the new pay method |

#### Return

Boolean return `true` on successful creation of a pay method.

#### Error

When an error occurs in the function call, an exception will be thrown with an appropriate message.
The most common messages are detailed below. Other exceptions could be thrown and need to be caught.

| Exception | Message | Notes |
| --------- | ------- | ----- |
| Exception | Client ID not found | Check the client ID. The client ID passed has not been found |
| Exception | Module Not Found | Check the gateway module name. The module name passed has not been found |
| Exception | Module Not Activated | The gateway module passed is not currently active |
| RuntimeException | Card number is required | The card number is required for a local storage gateway |
| RuntimeException | Card number must be at least 13 chars | For a local storage gateway, the card number should be at least 13 characters |
| RuntimeException | Card expiry date is required | For a local storage gateway, the card expiry date is required |
| InvalidArgumentException | Invalid Workflow Type for PayMethod | Only credit cards can be added using this function |

### updateCardPayMethod

This function can be used to update an existing card pay method for a client.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientId | int | The ID of the client that the pay method belongs to |
| payMethodId | int | The ID of the pay method to be updated |
| cardExpiryDate | string | Card expiry date in mmyy format |
| cardStartDate | null or string | Optional. Card start date in mmyy format |
| cardIssueNumber | null or string | Optional. The issue number for the card |
| remoteToken | string | Required for a remote pay method. The remote token for a remote pay method.

#### Return

Boolean return `true` on successful update of the pay method.

#### Error

When an error occurs in the function call, an exception will be thrown with an appropriate message.
The most common messages are detailed below. Other exceptions could be thrown and need to be caught.

| Exception | Message | Notes |
| --------- | ------- | ----- |
| Exception | Client ID not found | Check the client ID. The client ID passed has not been found |
| Exception | PayMethod ID not found | Check the pay method ID. The pay method ID passed has not been found |
| InvalidArgumentException | Invalid PayMethod | The pay method being updated is not a credit card |
| RuntimeException | Card expiry date is required | For a local storage gateway, the card expiry date is required |

### createBankPayMethod

This function can be used to add a new bank pay method to a client account.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientId | int | The ID of the client for the new pay method |
| gatewayName | string | The name of the module adding the pay method |
| accountType | string | The type of bank account being added, such as checking or savings. Defaults to 'checking' |
| routingNumber | string | Bank routing number. A blank string '' can be passed for remote tokens |
| accountNumber | string | Bank account number. A blank string '' can be passed for remote tokens |
| bankName | string | Name of the bank |
| accountHolderName | string | The bank account owner's name |
| remoteToken | string | Required for a remote pay method. The remote token for a remote pay method.
| billingContactId | string or integer | Optional. The ID of the billing contact to use. Defaults to 'billing' |
| description | string | The description for the new pay method |

#### Return

Boolean return `true` on successful creation of a pay method.

#### Error

When an error occurs in the function call, an exception will be thrown with an appropriate message.
The most common messages are detailed below. Other exceptions could be thrown and need to be caught.

| Exception | Message | Notes |
| --------- | ------- | ----- |
| Exception | Client ID not found | Check the client ID. The client ID passed has not been found |
| Exception | Module Not Found | Check the gateway module name. The module name passed has not been found |
| Exception | Module Not Activated | The gateway module passed is not currently active |
| InvalidArgumentException | Invalid Workflow Type for PayMethod | Only bank accounts can be added using this function |

### updateBankPayMethod

This function can be used to update an existing bank pay method for a client.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientId | int | The ID of the client for the new pay method |
| payMethodId | int | The ID of the pay method to be updated |
| accountType | string | The type of bank account being added, such as checking or savings. Defaults to 'checking' |
| routingNumber | string | Bank routing number. A blank string '' can be passed for remote tokens |
| accountNumber | string | Bank account number. A blank string '' can be passed for remote tokens|
| bankName | string | Name of the bank |
| accountHolderName | string | The bank account owner's name |
| remoteToken | string | Required for a remote pay method. The remote token for a remote pay method.

#### Return

Boolean return `true` on successful update of the pay method.

#### Error

When an error occurs in the function call, an exception will be thrown with an appropriate message.
The most common messages are detailed below. Other exceptions could be thrown and need to be caught.

| Exception | Message | Notes |
| --------- | ------- | ----- |
| Exception | Client ID not found | Check the client ID. The client ID passed has not been found |
| Exception | PayMethod ID not found | Check the pay method ID. The pay method ID passed has not been found |
| InvalidArgumentException | Invalid PayMethod | The pay method being updated is not a bank account |

[callbacks]: /payment-gateways/callbacks "Callback Files"
[github-sample]: https://github.com/WHMCS/sample-remote-input-gateway "Sample Remote Input Gateway module"
[github-bank-sample]: https://github.com/WHMCS/sample-remote-bank-gateway-module "Sample Remote Input Bank Gateway module on GitHub"
