+++
prev = "/themes/testing"
title = "Variables"
toc = true
weight = 50

+++

In the Smarty template language, template variables take the format `{$variable_name}`.

The following template parameters are made available to all pages.

| Parameter | Description |
| --------- | ----------- |
| {$BASE_PATH_CSS} | The base URL to common CSS assets. |
| {$BASE_PATH_FONTS} | The base URL to common font assets. |
| {$BASE_PATH_IMG} | The base URL to common image assets. |
| {$BASE_PATH_JS} | The base URL to common Javascript assets. |
| {$charset} | The configured character set. |
| {$client} | The currently logged in Client, or null if a client is not logged in. |
| {$companyname} | The configured company name. |
| {$date_day} | The current calendar day. |
| {$date_month} | The current calendar month. |
| {$date_year} | The current calendar year. |
| {$filename} | The basename of the current file requested by the web browser. |
| {$language} | The name of the language to display to the user. |
| {$loggedin} | true or false depending on if a client is logged in. |
| {$logo} | The path to the configured logo image. |
| {$pagetitle} | The current page's title. |
| {$reCaptchaPublicKey} | The configured reCAPTCHA site key. This can be an empty string if the WHMCS installation does not use Google reCAPTCHA. |
| {$systemNonSSLURL} | The configured non-SSL URL. |
| {$systemsslurl} | The configured SSL URL. |
| {$systemurl} | The URL to the WHMCS system. Either the SSL or non-SSL URL depending on whether the current page loaded via HTTPS. |
| {$template} | The name of the template used for display. |
| {$todaysdate} | The current date, presented in "l, jS F Y" format. |
| {$token} | A CSRF token to use on POST forms. |
| {$WEB_ROOT} | Your WHMCS system's base URL. |

For a complete listing of all variables available to you in a given template file, add the following line to your template file and then access the page which calls the template via a browser to receive a popup listing all available template data.

```
{debug}
```
