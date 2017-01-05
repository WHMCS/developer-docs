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
| contactId | int | The contact id of the user making the request if logged in as a sub-account |
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
| date | string | Can be 'now()' or a specific timestamp |
| to | string | Comma separated list of recipients |
| cc | string | Comma separated list of CC recipients |
| bcc | string | Comma separated list of BCC recipients |
| subject | string |  |
| message | string |  |

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

Runs prior to a client email being sent.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| messagename | string | The name of the email template being sent |
| relid | int | The related entity ID for the email being sent |

#### Response

An array of key/value pairs to be made available as additional email template merged fields. To abort the sending, return the key/value pair `abortsend=true`

#### Example Code

```
<?php

add_hook('EmailPreSend', 1, function($vars) {
    $merge_fields = [];
    $merge_fields['my_custom_var'] = "My Custom Var";
    $merge_fields['my_custom_var2'] = "My Custom Var2";
    if ($vars['messagename'] =='My Message Name' && $vars['relid'] == 2) {
        //Stop the email from sending a specific message and related id.
        $merge_fields['abortsend'] = true;
    }
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

Executes when updating currency exchange rates. All supported automatic update currencies are retured

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
| searchTerm | string |  |

#### Response

An array of additional responses to be appended to the search results.

#### Example Code

```
add_hook('IntelligentSearch', 1, function($vars) {
    $searchResults = array();

    // look for matches in client notes field
    $result = select_query(
        'tblclients',
        'id,firstname,lastname,email',
        array('notes' => $vars['searchTerm'])
    );
    while ($data = mysql_fetch_array($result)) {
        $searchResults[] = '<div class="searchresult">
            <a href="clientssummary.php?userid=' . $data['id'] . '">
                <strong>' . $data['firstname'] . ' ' . $data['lastname'] . '</strong>
                #' . $data['id'] . '<br />
                <span class="desc">' . $data['email'] . '</span>
            </a>
        </div>';
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

## PreAutomationTask

Executes before an automation task occurs

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| task | \Collection |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreAutomationTask', 1, function($vars) {
    // Perform hook code here...
});
```

