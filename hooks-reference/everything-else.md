+++
title = "Everything Else"
weight = 10

+++

The following hooks are provided for Everything Else related events.

## AffiliateActivation

Executes as an affiliate is being activated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affid | int | The new unique id for the affiliate (tblaffiliates). |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AffiliateActivation', 1, function($vars) {
    // Perform hook code here...
});
```

## AffiliateClickthru

Executes when a user has clicked an affiliate referral link.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affiliateId | int | The unique id of the affiliate that the link belongs to |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AffiliateClickthru', 1, function($vars) {
    // Perform hook code here...
});
```

## AffiliateCommission

Executes as affiliate commission is being applied to an affiliate to clear later.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affiliateId | int |  |
| referralId | int | The id of the referral |
| serviceId | int | The id of the referred service |
| commissionAmount | float | The amount of commission to be appplied |
| commissionDelayed | bool | Will the commission be delayed |
| clearingDate | null|string | The date the commission will apply |
| payout | bool | Will this commission be applied to the affiliate commissions |
| message | string | The reason commission will not be applied if `payout` is false |

#### Response

Return boolean values to override 'skipCommission' or 'payout'.

#### Example Code

```
<?php

//Skip applying the commission for affiliate 2
add_hook('AffiliateCommission', 1, function($vars) {
    $return = [];

    if ($vars['affiliateId'] == 2) {
        $return['skipCommission'] = true;
    }
    return $return;
});


//Ensure commission is applied for affiliate 3
add_hook('AffiliateCommission', 1, function($vars) {
    $return = [];

    if ($vars['affiliateId'] == 3) {
        $return['payout'] = true;
    }
    return $return;
});
```

## AffiliateWithdrawalRequest

Executes when an affiliate withdrawal request is submitted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affiliateId | int | The unique id of the affiliate making the request |
| userId | int | The user id of the user making the request |
| clientId | int | The client id being acted on |
| balance | float | The amount of commission the withdrawal request is for |

#### Response

Use the return to skip creating a ticket. Return a boolean value of skipTicket.

#### Example Code

```
<?php

//Do not open a ticket for affiliate 2
add_hook('AffiliateWithdrawalRequest', 1, function($vars) {
    $return = [];
    if ($vars['affiliateId'] == 2) {
        $return['skipTicket'] = true;
    }

    return $return;
});
```

## AfterConfigOptionsUpgrade

Executes after a product configurable options upgrade has been processed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| upgradeid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterConfigOptionsUpgrade', 1, function($vars) {
    // Perform hook code here...
});
```

## CCUpdate

Executes after CC details have been stored for a client or the remote storage functions completed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| cardtype | string |  |
| cardnum | string | Only if stored locally |
| cardcvv | string |  |
| expdate | string |  |
| cardstart | string |  |
| cardissue | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CCUpdate', 1, function($vars) {
    // Perform hook code here...
});
```

## CalcAffiliateCommission

Executes as the amount of commission is being calculated

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| affid | int |  |
| relid | int | The id of the referred service |
| amount | float | The amount the commission is being calculated on |
| commission | float |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('CalcAffiliateCommission', 1, function($vars) {
    // Perform hook code here...
});
```

## CustomFieldLoad

Executes when custom fields are being loaded

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| fieldid | int |  |
| relid | int | The related id for the field type. |
| value | string |  |

#### Response

Override the value of the custom field returning the "value" key.

#### Example Code

```
<?php

add_hook('CustomFieldLoad', 1, function($vars) {
    return array('value' => 'overridden value',);
});
```

## CustomFieldSave

Executes when custom fields are being saved

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| fieldid | int |  |
| relid | int | The related id for the field type. |
| value | string |  |

#### Response

Override the value of the custom field returning the "value" key.

#### Example Code

```
<?php

add_hook('CustomFieldSave', 1, function($vars) {
    return array('value' => 'overridden value',);
});
```

## EmailPreLog

Runs prior to email being logged.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| date | string | Current timestamp |
| to | string | Comma separated list of recipients |
| cc | string | Comma separated list of CC recipients |
| bcc | string | Comma separated list of BCC recipients |
| subject | string |  |
| message | string |  |
| attachments | array |  |

#### Response

Accepts a return of key/value pairs to override the parameters to be logged. Use the same names as the input parameters. Return `abortLogging` to abort logging of the email.

#### Example Code

```
<?php

//Do not log emails for userid 2
add_hook('EmailPreLog', 1, function($vars) {
    $return = [];

    if ($vars['userid'] == 2) {
        $return['abortLogging'] = true;
    }

    return $return;
});

//Override the saved subject of the email for userid 3
add_hook('EmailPreLog', 1, function($vars) {
    $return = [];

    if ($vars['userid'] == 3) {
        $return['subject'] = 'This subject is overridden';
    }

    return $return;
});
```

## EmailPreSend

Runs prior to any templated email being sent.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| messagename | string | The name of the email template being sent |
| relid | int | The related entity ID for the email being sent. |
| mergefields | array | Original mergefield data |

#### Response

An array of key/value pairs to be made available as additional email template merged fields. To abort the sending, return the key/value pair `abortsend=true`. To attach a file(s) to the email return an array of the following structure `['attachments'=>[['filename'=>'file1.pdf','data'=>'<file_content_1>'],['filename'=>'file2.png','data'=>'<file_content_2>'],...]]`.

#### Example Code

```
<?php

add_hook('EmailPreSend', 1, function($vars) {
    $merge_fields = [];
    if (!array_key_exists('my_custom_var', $vars['mergefields'])) {
        $merge_fields['my_custom_var'] = "My Custom Var";
        $merge_fields['my_custom_var2'] = "My Custom Var2";
    }
    if ($vars['messagename'] == 'My Message Name' && $vars['relid'] == 2) {
        //Stop the email from sending a specific message and related id.
        $merge_fields['abortsend'] = true;
    }
    $merge_fields['attachments'] = [
        [
            'filename' => 'invoice.pdf',
            'data' => file_get_contents('path/to/file.pdf'),
        ],
    ];

    return $merge_fields;
});
```

## EmailTplMergeFields

Executes when editing an email template.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| type | string | The type of email template being edited. |

#### Response

an Array of key -> value pairs of merge fields

#### Example Code

```
<?php

//Output additional merge fields in the list when editing an email template
add_hook('EmailTplMergeFields', 1, function($vars) {
    $merge_fields = [];
    $merge_fields['my_custom_var'] = "My Custom Var";
    $merge_fields['my_custom_var2'] = "My Custom Var2";
    return $merge_fields;
});
```

## FetchCurrencyExchangeRates

Executes when updating currency exchange rates. All supported automatic update currencies are returned

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| USD | float |  |
| GBP | float |  |

#### Response

An array of key -> value pairs to define or override additional exchange rates. The rate should be appropriate to the EUR currency.

#### Example Code

```
<?php

//Return an exchange rate for the XBT currency
add_hook('FetchCurrencyExchangeRates', 1, function($vars) {
    //Code here to fetch the the current exchange rate relative to EUR

    //Return exchange rate relative to 1 EUR
    return ['XBT' => 927.121,];
});
```

## IntelligentSearch

Executes as the Intelligent Search is being completed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| searchTerm | string | The term being searched for |
| numResults | int | The number of results to return |

#### Response

An array of additional search results. See example for array structure. A string response was supported in versions prior to WHMCS 7.7.

#### Example Code

```
<?php

add_hook('IntelligentSearch', 1, function ($vars) {
    /**
     * This is an example of array return for an Intelligent Search.
     * This format is supported in the blend WHMCS Admin Template.
     * Any template based on blend and updated to WHMCS 7.7+ is also supported.
     */
    $searchResults = array();

    // look for exact matches in client notes field
    $result = \WHMCS\Database\Capsule::table('tblclients')
        ->where('notes', $vars['searchTerm'])
        ->get();

    foreach ($result as $client) {
        $searchResults[] = [
            'title' => $client->firstname . ' ' . $client->lastname, // The title of the search result. This is required.
            'href' => 'clientssummary.php?userid=' . $client->id, // The destination url of the search result. This is required.
            'subTitle' => $client->email, // An optional subtitle for the search result.
            'icon' => 'fal fa-user', // A font-awesome icon for the search result. Defaults to 'fal fa-star' if not defined.
        ];
    }
    return $searchResults;
});
```

## LinkTracker

Executes when a link.php link is being used.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| linkid | int | The id of the link being followed |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LinkTracker', 1, function($vars) {
    // Perform hook code here...
});
```

## LogActivity

Executes after an activity log entry has been created.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| description | string |  |
| user | string |  |
| userid | int |  |
| ipaddress | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LogActivity', 1, function($vars) {
    // Perform hook code here...
});
```

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

## PayMethodMigration

Executes when legacy payment details are being migrated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| client | \WHMCS\User\Client | The Client Model |

#### Response

A gateway module name.

#### Example Code

```
<?php
add_hook('PayMethodMigration', 1, function($vars) {
    // Perform hook code here...
});
```

## PreEmailSendReduceRecipients

Runs prior to a client email being sent and allows selective removal of CC and BCC recipients.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| messagename | string | The name of the email template being sent |
| relid | int | The related entity ID for the email being sent |
| recipients | array | Array containing 'cc' and 'bcc' recipients. Each recipient will be an array containing 'email' and 'fullname' indices |

#### Response

An array with a 'cc' and 'bcc' list of recipients. Each recipient in those lists should be indexed with the original index hash as provided by $recipients argument. If an empty 'cc' or 'bcc' list provided, it will remove all 'cc' or 'bcc' recipients respectively. If the 'cc' or 'bcc' is omitted in the return, the original list will remain unaltered

#### Example Code

```
<?php
add_hook('PreEmailSendReduceRecipients', 1, function($vars) {
    // Perform hook code here...
});
```

## PreUpgradeCheckout

Executes on checkout of an upgrade order, after the price calculation. The upgrade order may have completed already when this hook runs.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientId | int | The ID of the client for the upgrade order |
| upgradeId | int | The ID of the upgrade order |
| serviceId | int | The ID of the service for the upgrade order |
| amount | float | The upgrade order amount. A negative value denotes a credit calculation. |
| discount | float | The upgrade order discount. |

#### Response

Return 'amount' and/or 'discount' key with override price for the upgrade order.

#### Example Code

```
<?php
add_hook('PreUpgradeCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## PremiumPriceOverride

Executes when searching for a premium domain. The return can alter the registration & renewal costs, stop the domain being available for purchase or force the client to contact support.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domainName | string |  |
| tld | string | eg com in whmcs.com |
| sld | string | eg whmcs in whmcs.com |
| register | float | If a registration, the registration price of the premium domain |
| transfer | float | If a transfer, the transfer price of the premium domain |
| renew | float | The renewal price of the premium domain |

#### Response

Accepts returns to override register, transfer or renew pricing. Also boolean values of noSale or contactUs to stop the sale of the domain with different messages

#### Example Code

```
<?php

//Stop the Domain Purchase for this Premium Domain
add_hook('PremiumPriceOverride', 1, function($vars) {
    return ['noSale' => true,];
});

//Force the Client to Contact Support to Purchase Domain
add_hook('PremiumPriceOverride', 1, function($vars) {
    return ['contactUs' => true,];
});

//Override the Register and Renew Pricing & Skip Markup Application
add_hook('PremiumPriceOverride', 1, function($vars) {
    return [
        'register' => 150.00,
        'renew' => 200.00,
        'skipMarkup' => true,
    ];
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

## VatNumberVerification

Verification of a VAT Number.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| vatNumber | \WHMCS\Billing\VAT\VatNumber |  |

#### Response

Constant from \WHMCS\Billing\VAT\Verification\VerificationInterface (STATE_VERIFIED, STATE_UNVERIFIED, or STATE_UNKNOWN)

#### Example Code

```
<?php
/**
 * Hook for VatNumberVerification must return a verification constant from
 * \WHMCS\Billing\VAT\Verification\VerificationInterface:
 * * STATE_VERIFIED - if the VAT number is registered
 * * STATE_UNVERIFIED - if the VAT number is not registered
 * * STATE_UNKNOWN - if the hook cannot determine the registration state of the
 *   VAT number
 *
 * Multiple hooks may be registered. When a hook responds with STATE_VERIFIED or
 * STATE_UNVERIFIED, the response is treated as authoritative and final.
 * By final:
 *  * when there are multiple hooks are registered, the first authoritative answer
 *    will be yielded to the application, and remaining registered hooks will not
 *    be consulted, and no additional integrated services will be consulted.
 *
 * If neither STATE_VERIFIED nor STATE_UNVERIFIED is yielded after process all
 * registered hooks, STATE_UNKNOWN will be used by the system. When the system
 * uses STATE_UNKNOWN, other integrated services of the system will be polled in
 * an attempt to get an authoritative, final response of STATE_VERIFIED or
 * STATE_UNVERIFIED.
 *
 * Two examples:
 * 1) a hook that uses custom logic for Ireland and Germany and all other EU regions
 * 2) a hook that allows some hypothetical test mode to give results for test numbers
 *
 * While these two could be in one hook, registering both illustrates the pipeline
 * for the verification request.
 */

add_hook('VatNumberVerification', 1, function($vars) {
    /** @var \WHMCS\Billing\VAT\VatNumber $vatNumber */
    $vatNumber = $vars['vatNumber'];
    $isValid = null;

    if ($vatNumber->getPrefix() == 'IE') {
        // Handle Ireland VAT numbers with custom logic
        $number = $vatNumber->getNumber(); // Example: '091234567'

        // custom logic here
        $isValid = customIrelandVatCheck($number);
    } elseif ($vatNumber->getPrefix() == 'DE') {
        // Handle Germany VAT numbers with custom logic
        $isValid = customGermanyVatCheck($vatNumber->getNumber());
    } elseif ($vatNumber->isEU()) {
        // Handle Germany VAT numbers with custom logic
        $isValid = customEuVatCheck($vatNumber->getNumber());
    }

    if ($isValid === false) {
        return \WHMCS\Billing\VAT\Verification\VerificationInterface::STATE_UNVERIFIED;
    } elseif ($isValid === true) {
        return \WHMCS\Billing\VAT\Verification\VerificationInterface::STATE_VERIFIED;
    } else {
        // let any other hook or the system give a final answer
        return \WHMCS\Billing\VAT\Verification\VerificationInterface::STATE_UNKNOWN;
    }
});

add_hook('VatNumberVerification', 1, function($vars) {
    /** @var \WHMCS\Billing\VAT\VatNumber $vatNumber */
    $vatNumber = $vars['vatNumber'];

    if ($someTestModeFlag) {
        if ($vatNumber->getIdentifier() == 'GB123456789') {
            return \WHMCS\Billing\VAT\Verification\VerificationInterface::STATE_VERIFIED;
        } elseif ($vatNumber->getIdentifier() == 'GB987654321') {
            return \WHMCS\Billing\VAT\Verification\VerificationInterface::STATE_UNVERIFIED;
        }
    }

    // let any other hook or the system give a final answer
    return \WHMCS\Billing\VAT\Verification\VerificationInterface::STATE_UNKNOWN;
});
```

