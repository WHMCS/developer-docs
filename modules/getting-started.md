+++
next = "/modules/code-samples/"
prev = "/modules/"
title = "Getting Started"
weight = 10

+++

The first step in creating a module for WHMCS is determining which type of module you wish to create:

* **[Provisioning Modules](/provisioning-modules/)** - Provisioning Modules, also referred to as Product or Server Modules, allow you to create modules to allow for the provisioning and management of products and services. [Learn more](/provisioning-modules/)

* **[Addon Modules](/addon-modules/)** - Addon Modules allow you to create modules and extensions that provide client and/or admin area output and that are not directly linked to individual products and services. [Learn more](/addon-modules/)

* **[Payment Gateway Modules](/payment-gateways/)** - Gateway Module allow you to connect WHMCS with additional payment and credit card processors for processing and capturing payments. Payment gateway modules include:
    - Third Party Gateways — A customer leaves the site to pay and returns when the payment process completes.
    - Merchant Gateways — A customer enters credit card details without leaving WHMCS and payment is processed via an API.
    - Tokenised Gateways — Credit card details are entered either within or outside of WHMCS and a token is generated and stored for future billing needs.

* **[Mail Provider Modules](/mail-providers/)** - Mail Provider Modules allow you to create modules to add custom mail providers within WHMCS. [Learn more](/mail-providers/)

* **[Registrar Modules](/domain-registrars/)** - Registrar Modules, also referred to as Domain Modules, allow you to create modules to allow for the registration and management of domains within WHMCS. [Learn more](/domain-registrars/)

Sample modules demonstrating usage and functionality are made available for all types of modules via the [WHMCS GitHub page](https://github.com/whmcs).

## Recommended Reading

* [Code Samples](/modules/code-samples/) - We make sample code available for each of our module types via GitHub.
* [Style Guide](/modules/style-guide/) - Recommended programming style and best practices for developing with WHMCS.
* [Module Class Autoloading](/modules/module-class-autoloading) — Enable automatic class loading in WHMCS modules.
* [Hooks Guide](/hooks/) - Hooks allow you to execute your own code when events occur inside WHMCS.
* [API Guide](/api/) - The API allows you to perform operations and actions within WHMCS.
