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
 * @param int $userId
 *
 * @return array
 */
$currencyData = getCurrency($userId);
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

See http://docs.whmcs.com/classes/7.0/WHMCS/View/Formatter/Price.html for more information.
