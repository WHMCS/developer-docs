+++
next = "/domain-registrars/premium-domains/"
prev = "/domain-registrars/domain-information/"
title = "Availability Checks"
weight = 80

+++

In WHMCS 7.1 and later, domain registrar modules can take control of Domain Availability checks and lookups.

There are two supported functions: `CheckAvailability` and `GetDomainSuggestions`

## Check Availability

The purpose of this function is to check if a domain is available for registration or transfer.

### Input Parameters

In addition to the regular [Common Module Parameters](/domain-registrars/module-parameters/), the CheckAvailability function is passed the following input parameters.

| Variable | Type | Description |
| --------- | ----------- | ----------- |
| searchTerm | string | The search term provided by the end user
| punyCodeSearchTerm | string | For an IDN domain, the puny code encoded search term
| tldsToInclude | array | An array of TLDs/extensions to perform the availability check for
| isIdnDomain | bool | If IDN Domains are enabled for this WHMCS installation
| premiumEnabled | bool | If Premium Domains are enabled for this WHMCS installation

{{% notice info %}}
For performance reasons, we recommending performing the lookup for all requested extensions at the same time if the registrar supports it.
{{% /notice %}}

### Return

The return of this function is expected to be an ArrayObject based collection of \WHMCS\Domains\DomainLookup\SearchResult results.

Each SearchResult object consists of an SLD and TLD, a status (available, registered, reserved) and optionally premium information such as Purchase Cost Price.

### Code Sample

Please refer to the example provided in the [Sample Registrar Module available via GitHub](https://github.com/WHMCS/sample-registrar-module) for an example implementation of the `CheckAvailability` function.

## Get Domain Suggestions

The purpose of this function is to return a list of alternative domain registration suggestions based on the search term provided by an end user.

### Input Parameters

In addition to the regular [Common Module Parameters](/domain-registrars/module-parameters/), the GetDomainSuggestions function is passed the following input parameters.

| Variable | Type | Description |
| --------- | ----------- | ----------- |
| searchTerm | string | The search term provided by the end user
| punyCodeSearchTerm | string | For an IDN domain, the puny code encoded search term
| tldsToInclude | array | An array of TLDs/extensions to perform the availability check for
| isIdnDomain | bool | If IDN Domains are enabled for this WHMCS installation
| premiumEnabled | bool | If Premium Domains are enabled for this WHMCS installation
| suggestionSettings | array | An array of settings and their values as defined in the `DomainSuggestionOptions` function

### Return

The return of this function is expected to be an ArrayObject based collection of \WHMCS\Domains\DomainLookup\SearchResult results.

All domains returned by the suggestions function should be available for registration.

### Code Sample

Please refer to the example provided in the [Sample Registrar Module available via GitHub](https://github.com/WHMCS/sample-registrar-module) for an example implementation of the `GetDomainSuggestions` function.

