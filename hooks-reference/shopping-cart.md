+++
title = "Shopping Cart"
weight = 10

+++

The following hooks are provided for Shopping Cart related events.

## AcceptOrder

Runs when an order is accepted prior to any acceptance actions being executed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The order ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AcceptOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonFraud

Executes when an addon is set as fraud.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonFraud', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterCalculateCartTotals

Executes after the cart totals have been calculated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| total | \Price | Total due today |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterCalculateCartTotals', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterFraudCheck

Executes after a fraud check has been completed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The id of the order that has been fraud checked |
| ordernumber | int | The order number |
| invoiceid | int | The ID of the invoice generated on order |
| amount | float | The amount the order was for |
| fraudresults | array | The full result from the fraud check |
| isfraud | bool | Has the check been deemed as fraud |
| frauderror | array | The details of the fraud check if an error occurs |
| clientdetails | array | The full details of the client the order is for |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterFraudCheck', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterShoppingCartCheckout

Upon completion of checkout once the order has been created, invoice generated and all email notifications sent.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| OrderID | int | The Order ID |
| OrderNumber | int | The randomly generated order number |
| ServiceIDs | array | An array of Service IDs created by the order |
| AddonIDs | array | An array of Addon IDs created by the order |
| DomainIDs | array | An array of Domain IDs created by the order |
| RenewalIDs | array | An array of Domain Renewal IDs created by the order |
| PaymentMethod | string | The payment gateway selected |
| InvoiceID | int | The Invoice ID |
| TotalDue | float | The total amount due |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterShoppingCartCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## CancelOrder

Runs when an order is requested to be cancelled, prior to the change of status actually occurring.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The order ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CancelOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## CartItemsTax

Invoked as tax is being calculated for both cart and checkout, this can be used to manipulate
the tax rate applied to the cart total or relevant checkout payment intents.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientData | array|null | An array of client data, if available. |
| cartData | \ItemInterface[] | An array of all data held within in the shopping cart. |

#### Response

Return an array of the manipulated ItemInterface items. Tax will
be calculated from the delta of the original items.

#### Example Code

```
<?php

use WHMCS\View\Formatter\Price;

add_hook('CartItemsTax', '1', function ($vars) {
    $cartItems = $vars['cartData'];
    $client = $vars['clientData'];

    // Calculate your tax rate to apply
    $taxRate = 1.5; // 50%

    /** @var \WHMCS\Cart\Item\ItemInterface $item */
    foreach ($cartItems as $item) {
        if (!$item->isTaxed()) {
            continue;
        }

        /** @var Price $amountToday */
        $amountToday = $item->getAmount();

        // Set the price due today for the item
        $item->setAmount(new Price(
            ($amountToday->toNumeric() * $taxRate),
            $amountToday->getCurrency()
        ));

        if ($item->isRecurring()) {
            /** @var Price $recurringAmount */
            $recurringAmount = $item->getRecurringAmount();
            // Set the recurring price of the item
            $item->setRecurringAmount(
                new Price(
                    ($recurringAmount->toNumeric() * $taxRate),
                    $recurringAmount->getCurrency()
                )
            );
        }
    }

    return [
        'cartData' => $cartItems
    ];
});
```

## CartSubdomainValidation

Executes when Cart Subdomain Validation is occurring

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| subdomain | string | eg sub in sub.whmcs.com |
| domain | string | eg whmcs.com in sub.whmcs.com |

#### Response

Return any validation errors. eg: return array('error1', 'error2',);

#### Example Code

```
<?php
add_hook('CartSubdomainValidation', 1, function($vars) {
    // Perform hook code here...
});
```

## CartTotalAdjustment

Invoked as the order total is being calculated, this can be used to manipulate the final total.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| products | array | An indexed array of products in the shopping cart. Keys include `pid`, `domain`, `billingcycle`, `configoptions`, `customfields`, `addons`, `server`, `hostname` |
| domains | array | An indexed array of domain registrations & transfers in the shopping cart. Keys include `type`, `domain`, `regperiod` |

#### Response

Return an array consisting of adjustment `description`, `amount` and `taxed` (bool)

#### Example Code

```
<?php

add_hook('CartTotalAdjustment', 1, function($vars) {
    $cart_adjustments = array();

    $products = $tlds = [];

    foreach ($vars['products'] as $product) {
        $products[] = $product['pid'];
    }

    foreach ($vars['domains'] as $domain) {
        if ($domain['type'] == 'register') {
            $domainParts = explode('.', $domain['domain'], 2);
            $tlds[] = $domainParts[1];
        }
    }

    if (in_array(1, $products) && in_array('co.uk', $tlds)) {
        $cart_adjustments = [
            "description" => "Custom discount for buying product 1 and a co.uk domain",
            "amount" => "-18.00",
            "taxed" => false,
        ];
    }
    return $cart_adjustments;
});
```

## DeleteOrder

Runs when an order is requested to be deleted, prior to the deletion actually occurring.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The order ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DeleteOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## FraudCheckAwaitingUserInput

Executes when the fraud check is awaiting user input.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The id of the order that has been fraud checked |
| ordernumber | int | The order number |
| invoiceid | int | The ID of the invoice generated on order |
| amount | float | The amount the order was for |
| fraudresults | array | The full result from the fraud check |
| isfraud | array | The details of the fraud check if an error occurs |
| clientdetails | array | The full details of the client the order is for |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FraudCheckAwaitingUserInput', 1, function($vars) {
    // Perform hook code here...
});
```

## FraudCheckFailed

Executes when the fraud check fails for a new order.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The id of the order that has been fraud checked |
| ordernumber | int | The order number |
| invoiceid | int | The ID of the invoice generated on order |
| amount | float | The amount the order was for |
| fraudresults | array | The full result from the fraud check |
| isfraud | array | The details of the fraud check if an error occurs |
| clientdetails | array | The full details of the client the order is for |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FraudCheckFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## FraudCheckPassed

Executes when the fraud check passes successfully for a new order.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The id of the order that has been fraud checked |
| ordernumber | int | The order number |
| invoiceid | int | The ID of the invoice generated on order |
| amount | float | The amount the order was for |
| fraudresults | array | The full result from the fraud check |
| isfraud | array | The details of the fraud check if an error occurs |
| clientdetails | array | The full details of the client the order is for |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FraudCheckPassed', 1, function($vars) {
    // Perform hook code here...
});
```

## FraudOrder

Runs when an order is requested to be set as fraud, prior to the change of status actually occurring.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The order ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FraudOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## OrderAddonPricingOverride

Executes as an addon price is being calculated in the cart.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| key | int | The key for the product in the cart session |
| pid | int | The product id |
| addonid | int | The addon id |
| proddata | array | The product data for an addon with new product purchase |
| serviceid | int | The service id when purchasing an addon for existing service |

#### Response

Addon pricing can be overridden. Accepts a return of the keys 'setup' and 'recurring'.

#### Example Code

```
<?php

use WHMCS\Service\Service;

add_hook('OrderAddonPricingOverride', 1, function($vars) {
    $return = [];
    if (array_key_exists('proddata', $vars)) {
        /**
         * This is a product and addon purchase
         */
        if ($vars['addonid'] == 1 && $vars['proddata']['pid'] == 1) {
            $return = ['setup' => '1.00', 'recurring' => '5.00',];
        }
    } else {
        /**
         * This is an addon only purchase for existing service
         */
        $serviceData = Service::find($vars['serviceid']);
        if ($serviceData && $vars['addonid'] == 1 && $serviceData->packageId == 1) {
            $return = ['setup' => '1.00', 'recurring' => '5.00',];
        }
    }
    return $return;
});
```

## OrderDomainPricingOverride

Executes as a domain price is being calculated in the cart.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| type | string | Either `register` or `transfer` |
| domain | string |  |
| regperiod | int | The registration period of the domain (in years) |
| renewalperiod | int | The renewal period of the domain (in years) |
| dnsmanagement | bool |  |
| emailforwarding | bool |  |
| idprotection | bool |  |
| eppcode | string | Available for transfer only. |
| isPremium | bool |  |

#### Response

A float to override the first payment, or an array to override first and/or recurring amounts

#### Example Code

```
<?php

add_hook('OrderDomainPricingOverride', 1, function($vars) {
    // Perform operations to determine price.
    // To override the first payment amount only simply return a float
    return '64.95';
    // To override the first payment and recurring amount, return an array as follows
    return ['firstPaymentAmount' => 64.95, 'recurringAmount' => 14.45];
});
```

## OrderPaid

Executes when the first invoice for a new order is marked paid. This will execute in addition to the regular invoice payment hooks.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderId | int | The unique identifier for the order |
| userId | int | The unique identifier for the client |
| invoiceId | int | The unique identifier for the invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('OrderPaid', 1, function($vars) {
    // Perform hook code here...
});
```

## OrderProductPricingOverride

Executes as a product price is being calculated in the cart.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| key | int | The key for the product in the cart session |
| pid | int | The product id |
| proddata | array | The product data |

#### Response

Product pricing can be overridden - exclusive of configurable option cost. Accepts a return of the keys 'setup' and 'recurring'. eg: return array('setup' => 1.00, 'recurring' => 12.00);

#### Example Code

```
<?php

use WHMCS\Authentication\CurrentUser;

add_hook('OrderProductPricingOverride', 1, function($vars) {
    $return = [];

    /**
     * Get the logged in client. Returns null if no client logged in.
     *
     * @see https://developers.whmcs.com/advanced/authentication/
     */
    $client = CurrentUser::client();

    /**
     * Run the following rules if a Client is logged in.
     */
    if ($client) {
        /**
         * Override the product price when ordering product 1 and the user has the ID 10.
         */
        if ($vars['pid'] == 1 && $client->id == 10) {
            $return = ['setup' => '0.00', 'recurring' => '0.00',];
        }

        /**
         * Override the product price when user has the ID 72.
         */
        if ($client->id == 72) {
            $return = ['setup' => '0.00', 'recurring' => '0.00',];
        }
    }
    return $return;
});
```

## OrderProductUpgradeOverride

Executes as a product upgrade order is being calculated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| oldproductid | int |  |
| oldproductname | string |  |
| newproductid | int |  |
| newproductname | string |  |
| days | int |  |
| totaldays | int |  |
| newproductbillingcycle | string |  |
| price | float |  |
| discount | float |  |
| promoqualifies | bool |  |

#### Response

Return any key -> value pairs of the parameters to override. eg return array('discount' => 10.00,);

#### Example Code

```
<?php

use WHMCS\Carbon;

add_hook('OrderProductUpgradeOverride', 1, function($vars) {
    $return = [];

    if ($vars['newproductid'] == 15) {
        /**
         * No promotion should be applied to product 15
         */
        $return['promoqualifies'] = false;
    }
    if (Carbon::now()->toDateString() == '2016-12-25') {
        /**
         * Offer half price upgrade on Christmas Day
         * This can also be done by halving the $vars['price'] and returning that.
         */
        $return['totaldays'] = round($vars['totaldays'] / 2);
    }
    return $return;
});
```

## OverrideOrderNumberGeneration

Executes prior to checkout. All cart information is passed to the hook.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| products | array | An indexed array of product information for each product in the cart. |
| domains | array | An indexed array of domain information for each domain in the cart. |

#### Response

Return the custom order number to be used (must be a valid numeric value).

#### Example Code

```
<?php

add_hook('OverrideOrderNumberGeneration', 1, function($vars) {
    // Generate and return a custom order number value (must be a valid integer).
    // We also recommend ensuring the custom number is unique.
    return time();
});
```

## PendingOrder

Runs when an order is requested to be set back to pending, prior to the change of status actually occurring.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The order ID |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PendingOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## PreCalculateCartTotals

Executes as the cart totals are being calculated. All cart information is passed to the hook. Examples given here.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| products | array | An indexed array of product information for each product in the cart. |
| domains | array | An indexed array of domain information for each domain in the cart. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreCalculateCartTotals', 1, function($vars) {
    // Perform hook code here...
});
```

## PreFraudCheck

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
|  $params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreFraudCheck', 1, function($vars) {
    // Perform hook code here...
});
```

## PreShoppingCartCheckout

Executes prior to checkout. All cart information is passed to the hook.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| products | array | An indexed array of product information for each product in the cart. |
| domains | array | An indexed array of domain information for each domain in the cart. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreShoppingCartCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## RunFraudCheck

Executes as the fraud module is being checked for an order.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |
| userid | int |  |

#### Response

Return any value to skip the fraud check

#### Example Code

```
<?php
add_hook('RunFraudCheck', 1, function($vars) {
    // Perform hook code here...
});
```

## ShoppingCartCheckoutCompletePage

Executes when the Complete Page is displayed on checkout.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int | The ID of the order |
| ordernumber | int | The order number for the order |
| invoiceid | int | The id of the invoice for the order |
| ispaid | bool | Indicates whether the order has been paid |
| amount | float | The amount of order |
| paymentmethod | string | The payment method of the order |
| clientdetails | array | The full details for the client the order is for |

#### Response

Return HTML to be displayed on the order complete page.

#### Example Code

```
<?php

add_hook('ShoppingCartCheckoutCompletePage', 1, function($vars) {
    /**
     * Redirect all orders to a different page after the order complete page is loaded.
     */
    return '<META http-equiv="refresh" content="5;URL=http://www.mydomain.com/ownpage.html" />';
});
```

## ShoppingCartValidateCheckout

Executes during checkout completion, which occurs before order and invoice creation. Use this to
prevent order creation and present errors to the user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| a | string | Value will be `checkout`. |
| submit | string | Value will be true. |
| promocode | string | If entered, a promotion code. |
| notes | string | If enabled, additional order notes |
| paymentmethod | string | The selected payment method |
| ccinfo | string | Either `new` or `useexisting`. |
| cctype | string |  |
| ccnumber | string |  |
| ccexpirymonth | string |  |
| ccexpiryyear | string |  |
| cccvv | string |  |
| custtype | string | Possible values are `new` or `existing` |
| clientId | int | A non-zero value if the user is authenticated during checkout. |
| loginemail | string | Value present only when the client authenticates during checkout. |
| loginpassword | string | Value present only when the client authenticates during checkout. |
| firstname | string | Value present when the client is new. |
| lastname | string | Value present when the client is new. |
| companyname | string | Value present when client is new |
| email | string | Value present when client is new |
| address1 | string | Value present when client is new |
| address2 | string | Value present when client is new |
| city | string | Value present when client is new |
| state | string | Value present when client is new |
| country | string | Value present when client is new; two letter ISO code |
| tax_id | string | The client's tax ID |
| phonenumber | string | Value present when client is new |
| password | string | Value present when client is new |
| password2 | string | Value present when client is new |
| securityqid | string | Value present when client is new |
| securityqans | string | Value present when client is new |
| customfield | array | Value present when client is new |

#### Response

Return accepts both a `string` or an `array`. Use a string for `single` error message or an `array` of strings for multiple error messages.

#### Example Code

```
<?php

add_hook('ShoppingCartValidateCheckout', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
});
```

## ShoppingCartValidateDomain

Executes when Cart Domain Validation is occurring

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domainoption | string |  |
| sld | string | eg whmcs in whmcs.com |
| tld | string | eg com in whmcs.com |

#### Response

Return any validation errors. eg: return array('error1', 'error2',);

#### Example Code

```
<?php

add_hook('ShoppingCartValidateDomain', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
});
```

## ShoppingCartValidateDomainsConfig

Executes when Domain Update is occurring

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | array | The REQUEST variables |

#### Response

Return accepts both a `string` or an `array`. Use a string for `single` error message or an `array` of strings for multiple error messages.

#### Example Code

```
<?php

add_hook('ShoppingCartValidateDomainsConfig', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
});
```

## ShoppingCartValidateProductUpdate

Executes when Product Update is occurring

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | array | The REQUEST variables |

#### Response

Return accepts both a `string` or an `array`. Use a string for `single` error message or an `array` of strings for multiple error messages.

#### Example Code

```
<?php

add_hook('ShoppingCartValidateProductUpdate', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
});
```

## ShoppingCartValidateUpgrade

Executes during an upgrade/downgrade request to validate resource limits.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | ID of the existing hosting service |
| pid | int | ID of the target product for upgrade |

#### Response

An array of error messages. Return an empty array to allow the upgrade.

#### Example Code

```
<?php

use WHMCS\Service\Service;
use WHMCS\Product\Product;

Hook::add('ShoppingCartValidateUpgrade', 1, function($vars) {
    try {
        $actualHosting = Service::findOrFail($vars['id']);
        $requestedUpgrade = Product::findOrFail($vars['pid']);

        if ($requestedUpgrade->overageDiskLimit == 0 && $requestedUpgrade->overageBandwidthLimit == 0) {
            return [];
        }

        if (
            $actualHosting->diskUsage > $requestedUpgrade->overageDiskLimit
            || $actualHosting->bandwidthUsage > $requestedUpgrade->overageBandwidthLimit
        ) {
            return [
                'Your current disk or bandwidth usage exceeds the limits of the chosen product. <br /><br />Please reduce usage or select a higher plan.',
            ];
        }
        return [];
    } catch (\Exception $e) {
        return [
            'Error message feedback error 1',
            'Error message feedback error 2',
        ];
    }
});
```

