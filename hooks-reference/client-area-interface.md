+++
title = "Client Area Interface"
weight = 10

+++

The following hooks are provided for Client Area Interface related events.

## ClientAreaPage

Executes on all pages of the client area and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPage', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAddContact

Executes on the client area add contact page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageAddContact', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAddFunds

Executes on the client area add funds page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageAddFunds', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAddonModule

Executes on client pages created by an addon module and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageAddonModule', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAffiliates

Executes on the client area affiliates page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageAffiliates', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAnnouncements

Executes on the client area announcements page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageAnnouncements', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageBanned

Executes on the banned user page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageBanned', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageBulkDomainManagement

Executes on the client area bulk domain management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageBulkDomainManagement', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCancellation

Executes on the client area cancellation request page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageCancellation', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCart

Executes on the shopping cart page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageCart', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageChangePassword

Executes on the client area change password page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageConfigureSSL

Executes on the client area SSL configuration page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageConfigureSSL', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageContact

Executes on the contact form page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageContact', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageContacts

Executes on the client area contacts/sub-accounts management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageContacts', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCreditCard

Executes on the client area manage credit card page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageCreditCard', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCreditCardCheckout

Executes on the credit card payment page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageCreditCardCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainAddons

Executes on the client area domain add-ons page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainAddons', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainChecker

Executes on the client area domain checker page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainChecker', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainContacts

Executes on the client area domain WHOIS contact information page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainContacts', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainDNSManagement

Executes on the client area domain DNS Host Record management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainDNSManagement', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainDetails

Executes on the client area domain overview page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainEPPCode

Executes on the client area domain EPP Code page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainEPPCode', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainEmailForwarding

Executes on the client area domain Email Forwarding rules page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainEmailForwarding', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainRegisterNameservers

Executes on the client area domain Register Private Nameservers page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomainRegisterNameservers', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomains

Executes on the client area domains list page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDomains', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDownloads

Executes on the client area downloads page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageDownloads', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageEmails

Executes on the client area email history page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageEmails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageHome

Executes on the client area homepage and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageHome', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageInvoices

Executes on the client area invoices page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageInvoices', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageKnowledgebase

Executes on the client area knowledgebase page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageKnowledgebase', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageLogout

Executes on the client area logout page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageLogout', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageMassPay

Executes on the client area mass invoice payment page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageMassPay', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageNetworkIssues

Executes on the client area network issues page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageNetworkIssues', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPagePasswordReset

Executes on the client area password reset page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPagePasswordReset', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageProductDetails

Executes on the client area product overview page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageProductDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageProductsServices

Executes on the client area product and services list page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageProductsServices', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageProfile

Executes on the client area profile page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageProfile', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageQuotes

Executes on the client area quotes page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageQuotes', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageRegister

Executes on the client registration page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageRegister', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageSecurity

Executes on the client area security page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageSecurity', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageServerStatus

Executes on the client area server status page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageServerStatus', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageUnsubscribe

Executes on the email unsubscribe page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageUnsubscribe', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageUpgrade

Executes on the client area upgrade/downgrade page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageUpgrade', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewEmail

Executes on the client area view email page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageViewEmail', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewInvoice

Executes on the client area view invoice page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageViewInvoice', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewQuote

Executes on the client area view quote page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageViewQuote', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewWHOIS

Executes on the client area view WHOIS information page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPageViewWHOIS', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPaymentMethods

Executes on the client area payment methods management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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
add_hook('ClientAreaPaymentMethods', 1, function($vars) {
    // Perform hook code here...
});
```

