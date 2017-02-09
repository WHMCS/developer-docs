+++
next = "/payment-gateways/third-party-gateway"
prev = "/payment-gateways"
title = "Getting Started"
toc = true
weight = 10

+++

## Introduction <a id="introduction"></a>

Gateway modules allow a connection between WHMCS and merchants that aren't supported in WHMCS.
This documentation will explain a module's structure and everything needed to create a gateway module for WHMCS.

## Getting Started <a id="getting-started"></a>

To get started, begin by downloading the module development kit from our GitHub site.
There are two sample modules available, depending upon the [type of gateway][module-type] being developed:

* Third Party Gateway: https://github.com/WHMCS/sample-gateway-module
* Merchant Gateway: https://github.com/WHMCS/sample-merchant-gateway

Take the gateway module template "template.php" from this download and rename it to "yourgatewayname.php".
It should be all lowercase and must start with a letter.
Prefix all functions within a gateway module with the filename.
Open the file and replace all occurrences of **template_** with **yourgatewayname_**

## Config Array <a id="config-array"></a>

Configure the yourgatewayname_config array.
This function is the primary function required by all gateway modules.
The function defines both the display name for the module, and any settings that the gateway module requires.
The available field types are "text", "dropdown", "textarea" and "yesno" (checkboxes).
The sample config array in "template.php" demonstrates how to use each of these types.
The general formula:

1. Specify a system name (all in lowercase for the setting to be referenced by in the module code itself)
2. A FriendlyName
3. Type
4. Any settings specific to that field type.

Any fields defined here will be available in all gateway module functions in the $params array.
Avoid common names like currency, invoiceid, etc, as these will conflict with the standard variables.

## Module Type <a id="module-type"></a>

Determine which type of module needs to be created from the 2 core types:

1. **Third Party Gateways** – Where a customer leaves the site to pay and returns when the payment process completes.
2. **Merchant Gateways** – Where a customer enters credit card details in WHMCS.
The payment processes in the background.
Can also include 3D Secure where the user leaves your site.

For a Third Party gateway go to [Third Party Gateway][third-party].
For a merchant gateway go to [Merchant Gateway][merchant-gateway].


[module-type]: #module-type
[third-party]: /payment-gateways/third-party-gateway "Third Party Gateway"
[merchant-gateway]: /payment-gateways/merchant-gateway "Merchant Gateway"
