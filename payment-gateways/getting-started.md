+++
next = "/payment-gateways/meta-data-params"
prev = "/payment-gateways"
title = "Getting Started"
toc = true
weight = 10

+++

Payment gateway modules allow you to connect and integrate WHMCS with additional payment service providers.

## Types of payment gateway

Before you begin, you need to determine the type of payment gateway module you will be creating.

There are 3 primary types of payment gateway module:

1. **Third Party Gateways** – Where a customer leaves the site to pay and returns when the payment process is complete. Examples include PayPal Standard, 2Checkout

2. **Merchant Gateways** – Where a customer enters credit card details in WHMCS. The payment processes in the background. Can also include 3D Secure where the user leaves your site. Examples include PayPal Pro, Authorize.net AIM

3. **Tokenised Gateways** - A variation of a merchant gateway where credit card details are not stored locally. Tokenised Gateways can be further broken down into two groups:

    i. Remote Storage - Where the customer enters credit card details within WHMCS but the card details are not stored locally within the database instead being submitted immediately to the payment gateway and only a token returned by the gateway being stored.

    ii. iFrame Gateways - Where the gateway payment checkout process is loaded within an iframe. Examples include SagePay Form, Quantum Vault

## Getting Started

To get started, begin by downloading the appropriate sample module from our [GitHub page](https://github.com/whmcs).

* Third Party Gateway: https://github.com/WHMCS/sample-gateway-module
* Merchant Gateway: https://github.com/WHMCS/sample-merchant-gateway

Take the gateway module example file within the repo and rename it to `yourgatewayname.php`.

The filename should be all lowercase and must start with a letter.

After renaming it, open the file and replace all occurrences of `gatewaymodule_` with `yourgatewayname_`.

All files within the `/modules/gateways/` directory should contain code that adheres to the expected format/functions found within a WHMCS gateway module. Non-WHMCS related files, such as success/failure return pages or library files, should be located within a directory dedicated to the gateway module itself, for example, `/modules/gateways/yourgatewayname`.

{{% notice info %}}
We recommend prefixing all functions within a gateway module with the filename to avoid naming conflicts.
{{% /notice %}}
