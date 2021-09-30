+++
next = "/advanced/logging/"
prev = "/advanced/date-functions/"
title = "Currency Formatting"
weight = 40

+++

The following helper functions are provided for formatting currency values.

## Get Clients Currency

```
/**
 * Get clients currency
 *
 * Required before making a call to formatCurrency
 *
 * @param int $clientId The database ID number of the client to retrieve the currency information from
 *
 * @return array
 */
$currencyData = getCurrency($clientId);
```

## Format Currency

```
/**
 * Format currency
 *
 * @param float $amount
 * @param int   $currencyId
 *
 * @return \WHMCS\View\Formatter\Price
 */
$price = formatCurrency($amount, $currencyData['id']);
```

The `$price` value returned will be an object. The default `__toString` response format is a fully formatted price output including prefix and suffix.

See https://classdocs.whmcs.com/8.1/WHMCS/View/Formatter/Price.html for more information.
