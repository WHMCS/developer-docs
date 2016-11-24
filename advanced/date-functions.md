+++
next = "/advanced/currency-formatting/"
prev = "/advanced/db-interaction/"
title = "Date Functions"
weight = 30

+++

The following date helper functions are made available to make it easier to work with dates in WHMCS.

## Todays Date

```
/**
 * Returns todays date
 *
 * By default returns the format defined in General Settings > Localisation > Date Format
 *
 * @param bool $applyClientDateFormat Set true to apply Localisation > Client Date Format
 *
 * @return string
 */
$todaysdate = getTodaysDate($applyClientDateFormat);
```

## From MySQL Date

```
/**
 * Formats a MySQL Date/Timestamp value to system settings
 *
 * @param string $datetimestamp The MySQL Date/Timestamp value
 * @param bool $includeTime Pass true to include the time in the result
 * @param bool $applyClientDateFormat Set true to apply Localisation > Client Date Format
 *
 * @return string
 */
$date = fromMySQLDate($date, $includeTime, $applyClientDateFormat);
```

## To MySQL Date

```
/**
 * Converts a date entered in the system setting format to a MySQL Date/Timestamp
 *
 * @param string $userInputDate
 *
 * @return string Format: 2016-12-30 23:59:59
 */
$date = toMySQLDate($date);
```
