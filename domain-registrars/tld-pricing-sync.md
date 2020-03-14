+++
prev = "/domain-registrars/transfer-policy-management/"
next = "/domain-registrars/extending-further/"
title = "TLD & Pricing Sync"
weight = 110

+++

In WHMCS 7.10 and later, the Registrar TLD & Pricing Sync Utility allows for a registrar module to support importing TLDs and pricing.

Users can use the Sync Utility to import TLDs and automatically apply a defined margin markup.

To integrate this functionality into your registrar module, you must define a `GetTldPricing` function that builds and returns a ResultList object containing ImportItems defining TLDs and their cost pricing.

| Method | Type | Required/Optional | Description |
| --------- | ----------- | ------ | ------ |
| setExtension | string | Required | The extension to import. Example: .com, .net, or .co.uk |
| setMinYears | int | Optional | The minimum number of years that the extension can be registered for. Default: 1 |
| setMaxYears | int | Optional | The maximum number of years that the extension can be registered for. Default: 10 |
| setYearsStep | int | Optional | The number of years between each registration period. Default: 1 |
| setRegisterPrice | float | Required | The registration cost price for the minimum registration period term. |
| setRenewPrice | float | Optional |  The renewal cost price for the minimum registration period term. Pass null if renewals are not supported. |
| setTransferPrice | float | Optional |  The transfer cost price for the minimum registration period term. Pass null if transfers are not supported. |
| setRedemptionFeePrice | float | Optional |  The redemption fee cost price for the extension. Pass null if redemption periods are not supported.  |
| setCurrency | string | Optional | The ISO4217 three letter currency code that registrar cost prices are defined in. This currency must exist within the WHMCS installation. eg. USD, GBP, etc.... Default: System Currency |
| setEppRequired | boolean | Optional |  Does the extension require an EPP code for transfer requests |

## Example Usage

```
use WHMCS\Domain\TopLevel\ImportItem;
use WHMCS\Results\ResultsList;

function modulename_GetTldPricing(array $params)
{
    // Perform API call to retrieve extension information
    // A connection error should return a simple array with error key and message
    // return ['error' => 'This error occurred',];

    $results = new ResultsList;

    foreach ($extensionData as $extension) {
        // All the set methods can be chained and utilised together.
        $item = (new ImportItem)
            ->setExtension($extension['tld'])
            ->setMinYears($extension['minPeriod'])
            ->setMaxYears($extension['maxPeriod'])
            ->setRegisterPrice($extension['registrationPrice'])
            ->setRenewPrice($extension['renewalPrice'])
            ->setTransferPrice($extension['transferPrice'])
            ->setRedemptionFeePrice($extension['redemptionFee'])
            ->setCurrency($extension['currencyCode'])
            ->setEppRequired($extension['transferSecretRequired']);

        $results[] = $item;
    }
    return $results;
}
```
