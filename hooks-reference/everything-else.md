+++
title = "Everything Else"
weight = 10

+++

The following hooks are provided for Everything Else related events.

## NotificationPreSend

Executes prior to a notification being sent to allow for additional conditional criteria to be applied and manipulation of the notification message.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| eventType | string | 'Ticket', 'Invoice', 'Order', 'Service', 'Domain', or 'API' |
| eventName | string |  |
| rule | \WHMCS\Notification\Rule | Notification rule that has been matched. |
| hookParameters | array |  |
| notification | \WHMCS\Notification\Contracts\NotificationInterface |  |

#### Response

No response supported

#### Example Code

```
<?php

add_hook('NotificationPreSend', 1, function($vars) {

    $eventType = $vars['eventType'];
    $eventName = $vars['eventName'];
    $rule = $vars['rule'];
    $hookParameters = $vars['hookParameters'];
    $notification = $vars['notification'];

    // Perform additional conditional logic and throw the AbortNotification
    // exception to prevent the notification from sending.
    if ($eventType == 'Invoice'
        && $eventName == 'created'
        && (isset($hookParameters['invoiceid'])
            && $hookParameters['invoiceid'] > 1000)
    ) {
        throw new \WHMCS\Notification\Exception\AbortNotification();
    }

    // If allowing the notification to continue, you can manipulate the $notification
    // object using the interface, WHMCS\Notification\Contracts\NotificationInterface.
    $notification->setTitle('Override notification title');
    $notification->setMessage('Override notification message body');

});
```

## PremiumPriceRecalculationOverride

Executes when a premium domain price is being automatically recalculated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domainName | string | The full domain name. |
| tld | string | The TLD of the domain (E.g. com in whmcs.com) |
| sld | string | The SLD of the domain (E.g. whmcs in whmcs.com) |
| renew | float | The current renewal cost of the domain before any applied markup. |

#### Response

This return is accepted to override the renewal price or skip applying markup. E.g. return array('renew' => 50.00, 'skipMarkup' => true);

#### Example Code

```
<?php
add_hook('PremiumPriceRecalculationOverride', 1, function($vars) {
    // Perform hook code here...
});
```

