+++
next = "/domain-registrars/transfer-policy-management/"
prev = "/domain-registrars/availability-checks/"
title = "Premium Domains"
weight = 90

+++

In WHMCS 7.1 and later, registrar modules can include support for the selling of Premium Domains.

Premium Domains cannot be detected with traditional WHOIS lookups, and therefore to use Premium Domains, it requires a registrar module to implement the [Availability Check](/domain-registrars/availability-checks/) functions.

## How It Works

Premium Domain functionality must be enabled by admin users before it can be used. The status is passed as a boolean value to both the CheckAvailability and GetSuggestions registrar module functions under the parameter `premiumEnabled`.

When enabled, domain availability checks must return if a domain is premium, and if it is, also return pricing information.

The cost price of the registration will then be converted into the end users currency, and a markup as defined by the WHMCS admin user will be applied before displaying the price to the end user.

The registration and renewal registrar module functions will be passed two additional parameters when Premium Domains are enabled:

| Variable | Type | Description |
| --------- | ----------- | ----------- |
| premiumEnabled | bool | If Premium Domains are enabled for this WHMCS installation
| premiumCost | float | The cost price for the action being performed (registration or renewal)

{{% notice info %}}
If the cost price passed to the Register or Renew functions by WHMCS does not match the cost price of the domain at the time the action is being performed, the process should be aborted and an appropriate error message should be returned for the admin user.
{{% /notice %}}

### Code Sample

Please refer to the example provided in the [Sample Registrar Module available via GitHub](https://github.com/WHMCS/sample-registrar-module) for an example implementation of the `CheckAvailability` and `Register` functions. Both include the appropriate parameters for Premium Domain handling.
