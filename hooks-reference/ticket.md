+++
title = "Ticket"
weight = 10

+++

The following hooks are provided for Ticket related events.

## AdminAreaViewTicketPage

Executes when an admin views a support ticket within the admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |

#### Response

Returned HTML will be output to the page.

#### Example Code

```
<?php

use WHMCS\Session;
use WHMCS\Ticket\Watchers;

add_hook('AdminAreaViewTicketPage', 1, function($vars) {
    $return = '';
    $adminId = Session::get('adminid');

    $adminWatchingTickets = Watchers::byAdmin($adminId)->pluck('ticket_id')->toArray();

    if (in_array($vars['ticketid'], $adminWatchingTickets)) {
        $return = '<div class="alert alert-info" role="alert">You are watching this ticket</div>';
    }
    return $return;
});
```

## AdminAreaViewTicketPageSidebar

Executes when an admin views a support ticket within the admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |

#### Response

Returned HTML will be output to the sidebar.

#### Example Code

```
<?php
add_hook('AdminAreaViewTicketPageSidebar', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminSupportTicketPagePreTickets

Executes prior to aggregation and output of the support tickets listing page within the admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

Returned HTML will be output to the page.

#### Example Code

```
<?php
add_hook('AdminSupportTicketPagePreTickets', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageSubmitTicket

Executes on the client area ticket submission page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| companyname | string |  |
| logo | string |  |
| systemurl | string |  |
| charset | string |  |
| pagetitle | string |  |
| filename | string |  |
| template | string |  |
| language | string |  |
| LANG | array | Active language translation strings |
| todaysdate | string | Human friendly formatted version of todays date |
| date_day | string | Current day of the month |
| date_month | string | Current month |
| date_year | string | Current year |
| WEB_ROOT | string | The web path to the WHMCS doc root |
| BASE_PATH_CSS | string |  |
| BASE_PATH_JS | string |  |
| BASE_PATH_FONTS | string |  |
| BASE_PATH_IMG | string |  |
| token | string | CSRF token value |
| servedOverSsl | bool | True if page was loaded via `https://` |

#### Response

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageSubmitTicket', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageSupportTickets

Executes on the client area support tickets overview page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| companyname | string |  |
| logo | string |  |
| systemurl | string |  |
| charset | string |  |
| pagetitle | string |  |
| filename | string |  |
| template | string |  |
| language | string |  |
| LANG | array | Active language translation strings |
| todaysdate | string | Human friendly formatted version of todays date |
| date_day | string | Current day of the month |
| date_month | string | Current month |
| date_year | string | Current year |
| WEB_ROOT | string | The web path to the WHMCS doc root |
| BASE_PATH_CSS | string |  |
| BASE_PATH_JS | string |  |
| BASE_PATH_FONTS | string |  |
| BASE_PATH_IMG | string |  |
| token | string | CSRF token value |
| servedOverSsl | bool | True if page was loaded via `https://` |

#### Response

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageSupportTickets', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewTicket

Executes on the client area view ticket page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| companyname | string |  |
| logo | string |  |
| systemurl | string |  |
| charset | string |  |
| pagetitle | string |  |
| filename | string |  |
| template | string |  |
| language | string |  |
| LANG | array | Active language translation strings |
| todaysdate | string | Human friendly formatted version of todays date |
| date_day | string | Current day of the month |
| date_month | string | Current month |
| date_year | string | Current year |
| WEB_ROOT | string | The web path to the WHMCS doc root |
| BASE_PATH_CSS | string |  |
| BASE_PATH_JS | string |  |
| BASE_PATH_FONTS | string |  |
| BASE_PATH_IMG | string |  |
| token | string | CSRF token value |
| servedOverSsl | bool | True if page was loaded via `https://` |

#### Response

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageViewTicket', 1, function($vars) {
    // Perform hook code here...
});
```

## SubmitTicketAnswerSuggestions

Executes prior to looking up knowledgebase article suggestions related to the message body of a ticket. Can be used to override the default knowledgebase lookup. If fewer than 5 results are returned, WHMCS will search the knowldebase and add its own results to the output.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| text | string | The message body |

#### Response

An array of knowledgebase article IDs.

#### Example Code

```
<?php
add_hook('SubmitTicketAnswerSuggestions', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketAddNote

Executes when a ticket note is added.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| message | string |  |
| adminid | int |  |
| attachments | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketAddNote', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketAdminReply

Executes when a reply is added to a ticket by an admin user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| replyid | int |  |
| deptid | int |  |
| deptname | string |  |
| subject | string |  |
| message | string |  |
| priority | string |  |
| admin | string | Admin user display name |
| status | string | Ticket status post reply |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketAdminReply', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketClose

Executes when a ticket is closed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketClose', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketDelete

Executes when a ticket is deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketId | int |  |
| adminId | int | The admin ID who initiated the action |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketDeleteReply

Executes when a ticket reply is deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketId | int |  |
| replyId | int |  |
| adminId | int | The admin ID who initiated the action |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketDeleteReply', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketDepartmentChange

Executes as a ticket department is changed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| deptid | int |  |
| deptname | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketDepartmentChange', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketFlagged

Executes as a ticket is flagged

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| adminid | int |  |
| adminname | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketFlagged', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketMerge

Executes when tickets are merged into each other.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| mergedTicketIds | array | The ticket IDs to be merged. |
| masterTicketId | int | The ticket ID of the ticket containing the merged tickets. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketMerge', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketOpen

Executes when a ticket is opened by an end user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| ticketmask | string |  |
| userid | int |  |
| deptid | int |  |
| deptname | string |  |
| subject | string |  |
| message | string |  |
| priority | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketOpen', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketOpenAdmin

Executes when a ticket is opened by an admin user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| ticketmask | string |  |
| userid | int |  |
| deptid | int |  |
| deptname | string |  |
| subject | string |  |
| message | string |  |
| priority | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketOpenAdmin', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketOpenValidation

Executes when an end user provides data for a new ticket submission.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| clientId | int | Client ID if associated with a client |
| contactId | int | Contact ID if associated with a contact |
| name | string | Name from email envelope if not a client |
| email | string | Email from email envelope if not a client |
| isAdmin | bool | TRUE if initiated within Admin Area or via API with input $admin=TRUE |
| departmentId | int |  |
| subject | string |  |
| message | string |  |
| priority | string |  |
| relatedService | string |  |
| customfields | array |  |

#### Response

A string to be used as a singular Validation Error.

#### Example Code

```
<?php
add_hook('TicketOpenValidation', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketPiping

Executes when a ticket is being imported via email.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| to | string |  |
| cc | array |  |
| name | string |  |
| email | string |  |
| subject | string |  |
| body | string |  |
| attachments | string |  |

#### Response

Return skipProcessing=true to abort importing of the given email.

#### Example Code

```
<?php
add_hook('TicketPiping', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketPriorityChange

Executes when a ticket priority is changed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| priority | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketPriorityChange', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketSplit

Executes when ticket replies are being split into a new ticket.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| originalTicketId | int | The Ticket ID that replies originally resided within. |
| newTicketID | int | The new Ticket ID for the split replies. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketSplit', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketStatusChange

Executes as a ticket status is changed manually by an admin.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| adminid | int |  |
| status | string |  |
| ticketid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketStatusChange', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketSubjectChange

Executes when a ticket subject is changed. The 'subject' variable now contains the new subject.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| subject | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketSubjectChange', 1, function($vars) {
    // Perform hook code here...
});
```

## TicketUserReply

Executes when a reply is added to a ticket by an end user.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| ticketid | int |  |
| replyid | int |  |
| userid | int |  |
| deptid | int |  |
| deptname | string |  |
| subject | string |  |
| message | string |  |
| priority | string |  |
| status | string | Ticket status post reply |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('TicketUserReply', 1, function($vars) {
    // Perform hook code here...
});
```

## TransliterateTicketText

Invoked when a ticket is imported from email.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| subject | string | The message subject |
| message | string | The message body |

#### Response

Override the global variables $subject and $message to manipulate.

#### Example Code

```
<?php
add_hook('TransliterateTicketText', 1, function($vars) {
    // Perform hook code here...
});
```

