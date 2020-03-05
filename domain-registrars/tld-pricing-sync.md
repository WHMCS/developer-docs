+++
prev = "/domain-registrars/transfer-policy-management/"
next = "/domain-registrars/extending-further/"
title = "TLD & Pricing Sync"
weight = 110

+++

In WHMCS 7.10 and later, the Registrar TLD & Pricing Sync Utility allows for a registrar module to support importing TLDs and pricing.

This feature introduces a single new function `GetTldPricing`. This function allows a registrar module to build and return an array object with the tld and pricing.

| Function | Type | Description |
| --------- | ----------- | ------ |
| setExtension | string | The extension to import. Example: .com, .net, or .co.uk |
| setCurrency | string | The ISO4217 three letter currency code of the registrar that will be used for all pricing. The currency should exist in WHMCS |
| setMinYears | int | The minimum number of years that an extension can be registered for. Default: 1 (optional) |
| setMaxYears | int | The maximum number of years that an extension can be registered for. Default: 10 (optional) |
| setYearsStep | int | The number of years between each registration period. Default: 1 (optional) |
| setRegisterPrice | float | The registration price for the minimum registration period in the registrar currency |
| setRenewPrice | float | The renewal price for the minimum registration period in the registrar currency. Not setting, or setting to a `null` value will disable renewals for the extension |
| setTransferPrice | float | The transfer price for the minimum registration period in the registrar currency. Not setting, or setting to a `null` value will disable transfers for the extension | 
| setRedemptionFeePrice | float | The redemption fee price for the extension (optional) |
| setEppRequired | boolean | Does the extension require an EPP code for transfer requests (optional) |

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
            ->setCurrency($extension['currencyCode'])
            ->setMinYears($extension['minPeriod'])
            ->setMaxYears($extension['maxPeriod'])
            ->setRegisterPrice($extension['registrationPrice'])
            ->setRenewPrice($extension['renewalPrice'])
            ->setTransferPrice($extension['transferPrice'])
            ->setEppRequired($extension['transferSecretRequired']);

        if ($extension['supportsRedemptionPeriod']) {
            $item->setRedemptionFeePrice($extension['redemptionFee']);
        }
        $results[] = $item;
    }
    return $results;
}
```
