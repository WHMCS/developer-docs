+++
next = "/payment-gateways/reversals"
prev = "/payment-gateways/refunds"
title = "Subscription Management"
toc = true
weight = 43

+++

Subscription Management is an optional function that can be defined within a gateway module. Its purpose is to remotely cancel a recurring subscription agreement with a payment gateway, manually and automatically. The stored Subscription ID value in WHMCS is then removed.

When a service is assigned to a payment gateway that implements this function (for example PayPal Subscriptions) and a Subscription ID is set, a **Cancel Subscription** button is displayed under the Products/Services tab in the admin area. Clicking it will trigger the API call defined in the _cancelSubscription function.

## Automatic Cancellation

When the **Automatic Subscription Management** feature is enabled under *Setup > General Settings > Invoices tab*, a subscription will be cancelled automatically under the following circumstances:

* A cancellation request is submitted
* The order is cancelled or set to fraud via the admin interface of WHMCS
* The API is used to cancel or fraud an order with “cancelsub=true” passed
* An upgrade order is placed for the product/service

## Implementing in payment gateway modules

This feature should only be defined for payment gateways which create automatic recurring subscriptions that are processed outside of WHMCS (for example PayPal Subscriptions).

Implementation is a two-step process:

1. A subscription ID must be stored in tblhosting.subscriptionid for the given service in order for the cancel subscription function to be invocable. Typically this value should be set as part of a payment gateway callback routine (see [callbacks](https://developers.whmcs.com/payment-gateways/callbacks/))

2. Define the _cancelSubscription function in the gateway module file.

This function should contain the necessary API calls to cancel a recurring payment subscription at the payment gateway.

Return a "success" response to indicate successful subscription cancellation. The stored tblhosting.subscriptionid value is then removed.
Any other response is considered a failure, and the subscriptionid value will remain in place.

An example of this function is shown in the sample gateway module at [Sample Gateway Module](https://github.com/WHMCS/sample-gateway-module/blob/master/modules/gateways/gatewaymodule.php)
