+++
title = "Ticket"
weight = 10

+++

The following hooks are provided for Ticket related events.

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

