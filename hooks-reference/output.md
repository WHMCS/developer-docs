+++
title = "Output"
weight = 10

+++

The following hooks are provided for Output related events.

## FormatDateForClientAreaOutput

Allows for transformation of a date prior to output within the Client Area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| date | \Carbon | A Carbon object representing the date/time. |

#### Response

Return a string containing the formatted date to display.

#### Example Code

```
<?php

add_hook('FormatDateForClientAreaOutput', 1, function ($vars) {
    // Perform hook code here...
});
```

## FormatDateTimeForClientAreaOutput

Allows for transformation of a date/time prior to output within the Client Area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| date | \Carbon | A Carbon object representing the date/time. |

#### Response

Return a string containing the formatted date and time to display.

#### Example Code

```
<?php

add_hook('FormatDateTimeForClientAreaOutput', 1, function ($vars) {
    // Perform hook code here...
});
```

