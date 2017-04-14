+++
title = "Client"
weight = 10

+++

The following hooks are provided for Client related events.

## AfterClientMerge

Executes after a client merge has completed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| toUserID | int | The id of the user being merged into. |
| fromUserID | int | The id of the user being merged from. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterClientMerge', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAdd

Executes as a client is being added to WHMCS.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| firstname | string |  |
| lastname | string |  |
| companyname | string |  |
| email | string |  |
| address1 | string |  |
| address2 | string |  |
| city | string |  |
| state | string |  |
| postcode | string |  |
| country | string |  |
| phonenumber | string |  |
| password | string |  |
| customFields | array |  |
| taxexempt | bool |  |
| latefeeoveride | bool |  |
| overideduenotices | bool |  |
| separateinvoices | bool |  |
| disableautocc | bool |  |
| emailoptout | bool |  |
| overrideautoclose | bool |  |
| notes | string |  |
| groupid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAlert

Executes when Client Alerts are being defined

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | \WHMCS\User\Client | The client model |

#### Response

Return a new alert object for rendering.

#### Example Code

```
<?php

use WHMCS\User\Alert;

add_hook('ClientAlert', 1, function($client) {
    $firstName = $client->firstName;
    $lastName = $client->lastName;
    return new Alert(
        "This is a test notification for {$firstName} {$lastName}",
        'info' //see http://getbootstrap.com/components/#alerts
    );
});
```

## ClientChangePassword

Executed when a change of password occurs for a client.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| password | string | The new password |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientClose

Executes after a client has been closed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientClose', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientDelete

Executes as a client is deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientDetailsValidation

Executes before adding a client or updating a client through the Admin or Client area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| firstname | string | The client's firstname |
| lastname | string | The client's lastname |
| companyname | string | The client's company, if entered |
| email | string | The client's email |
| address1 | string | The client's address1 |
| address2 | string | The client's address2, if entered |
| city | string | The client's city |
| state | string | The client's state |
| postcode | string | The client's postcode/zipcode |
| country | string | The client's country (2 character code) |
| phonenumber | string | The client's phone number |
| paymentmethod | string | If selected, the client's default payment method |
| customfield | string | An array of Key => Value pairs |
| securityqid | int | Only from Admin Area or when registering |
| securityqans | string | Only from Admin Area or when registering |

#### Response

Return accepts both a `string` or an `array`. Use a string for `single` error message or an `array` of strings for multiple error messages.

#### Example Code

```
<?php

add_hook('ClientDetailsValidation', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
});
```

## ClientEdit

Executes when a client is edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| uuid | string |  |
| firstname | string |  |
| lastname | string |  |
| companyname | string |  |
| email | string |  |
| address1 | string |  |
| address2 | string |  |
| city | string |  |
| state | string |  |
| postcode | string |  |
| country | string |  |
| phonenumber | string |  |
| password | string | The encrypted password for the user |
| currency | int | The id of the currency |
| notes | string |  |
| status | string |  |
| taxexempt | bool |  |
| latefeeoveride | bool |  |
| overideduenotices | bool |  |
| separateinvoices | bool |  |
| disableautocc | bool |  |
| emailoptout | bool |  |
| overrideautoclose | bool |  |
| language | string |  |
| billingcid | int |  |
| securityqid | int |  |
| securityqans | string | The encrypted security question answer |
| groupid | int | The id of the client group |
| allow_sso | bool | Is Single Sign on enabled for the client? |
| olddata | array | An array of the previous contact information |
| authmodule | string | The 2Factor Auth Module enabled for the user |
| authdata | string | The 2Factor Auth Data for the user |
| email_verified | bool |  |
| olddata | array | An array of the previous user information |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientEmailVerificationComplete

Executes upon successful completion of email verification by a client user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userId | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientEmailVerificationComplete', 1, function($vars) {
    // Perform hook code here...
});
```

## PreDeleteClient

Executes immediately before a client is deleted

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreDeleteClient', 1, function($vars) {
    // Perform hook code here...
});
```

