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
| isfraud | array | The details of the fraud check if an error occurs |
| clientdetails | array | The full details of the client the order is for |

Note: $vars is formatted as follows for maxmind fraud checking:

[0] => Array ( 
		[orderid] => 1234 
		[ordernumber] => 1223456
		[fraudresults] => Array (
        	[distance] => 1927 
			[countryMatch] => Yes 
			[countryCode] => US 
			[freeMail] => No 
			[anonymousProxy] => No 
			[score] => 5.46 
			[binMatch] => Yes 
			[binCountry] => US 
			[err] => 
			[proxyScore] => 1.80 
			[ip_region] => VA 
			[ip_city] => Herndon 
			[ip_latitude] => 38.0000 
			[ip_longitude] => -75.1234 
			[binName] => 
			[ip_isp] => Telia Network Services 
			[ip_org] => Telia Network Services 
			[binNameMatch] => NA 
			[binPhoneMatch] => NA 
			[binPhone] => 
			[custPhoneInBillingLoc] => NotFound 
			[highRiskCountry] => No 
			[queriesRemaining] => 1234 
			[cityPostalMatch] => Yes 
			[shipCityPostalMatch] => Yes 
			[maxmindID] => MMIDNUM1 
			[carderEmail] => No 
			[shipForward] => No 
			[highRiskPassword] => No 
			[riskScore] => 99.00 
			[explanation] => You should review this order carefully, as it is considered high risk. We suggest you be very cautious about accepting this order. This order is risky, as it might have come from an open proxy. This order is higher risk because the distance between the billing address and the user's actual location is so great 
			[error] => Array ( 
				[title] => MaxMind Error 
				[description] => MaxMind has deemed your order to be potentially high risk and therefore it has been held for manual review.<br /><br />If you feel you have received this message in error, then please accept our apologies and <a href="submitticket.php">submit a support ticket</a> to our Customer Service Team. Thank you. 
			) 
			[fraudoutput] => RAWOUTPUT 
		) 
        [invoiceid] => 123456 
		[amount] => 129.00 
		[isfraud] => Array ( 
			[title] => MaxMind Error 
			[description] => MaxMind has deemed your order to be potentially high risk and therefore it has been held for manual review.<br /><br />If you feel you have received this message in error, then please accept our apologies and <a href="submitticket.php">submit a support ticket</a> to our Customer Service Team. Thank you. 
		) 

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

Executes as an order is being cancelled

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CancelOrder', 1, function($vars) {
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

Executes as an order is being deleted

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('DeleteOrder', 1, function($vars) {
    // Perform hook code here...
});
```

## FraudOrder

Executes as an order is being marked fraud

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |

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

## OrderProductPricingOverride

Executes as a product price is being calculated in the cart.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| key | int | The key for the product in the cart session |
| pid | int | The product id |
| proddata | array | The product data |

#### Response

Product pricing can be overridden. Accepts a return of the keys 'setup' and 'recurring'. eg: return array('setup' => 1.00, 'recurring' => 12.00);

#### Example Code

```
<?php

use WHMCS\Session;

add_hook('OrderProductPricingOverride', 1, function($vars) {
    $return = [];

    /**
     * Override the product price when ordering product 1 and the user has the id 10
     */
    if ($vars['pid'] == 1 && Session::get('userid') == 10) {
        $return = ['setup' => '0.00', 'recurring' => '0.00',];
    }

    /**
     * Override the product price when user has the id 72
     */
    if (Session::get('userid') == 72) {
        $return = ['setup' => '0.00', 'recurring' => '0.00',];
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

use Carbon\Carbon;

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

Executes just before checkout occurs. All cart information is passed to the hook. Examples given here.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| products | array | An indexed array of product information for each product in the cart. |
| domains | array | An indexed array of domain information for each domain in the cart. |

#### Response

Return an overridden client displayed order number. eg: return array(123456788,);

#### Example Code

```
<?php

add_hook('OverrideOrderNumberGeneration', 1, function($vars) {
    /**
     * The order number should be validated to ensure it is unique
     */
    return [time()];
});
```

## PendingOrder

Executes as an order is being marked pending

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |

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

## PreShoppingCartCheckout

Executes just before checkout occurs. All cart information is passed to the hook. Examples given here.

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

HTML to be displayed on the order complete page.

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

## ViewOrderDetailsPage

Executes as the order details page is being displayed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |
| ordernum | int |  |
| userid | int |  |
| amount | float |  |
| paymentmethod | string |  |
| invoiceid | int |  |
|  | string | status |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ViewOrderDetailsPage', 1, function($vars) {
    // Perform hook code here...
});
```

