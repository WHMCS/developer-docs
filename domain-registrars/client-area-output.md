+++
prev = "/domain-registrars/module-logging/"
title = "Client Area Output"
weight = 100
+++

Using this function, it is possible to output custom HTML in the Client Area when a client is managing a domain name. 

Using the `_ClientArea` function, you can return output that will be shown in the Domain Overview when viewing a domain in the Client Area. 

All the parameters available in other registrar module functions are available to you within this function. 
Visit the [Module Parameters](https://developers.whmcs.com/domain-registrars/module-parameters/) page for information on  the variables available in `$params`. 

The function should return the HTML to be rendered on the page. 

Note: We recommend avoiding making remote API calls within this function as doing so will result in increased overheads for page 
load and potentially slower page load times.

```
/**
 * Client Area Output.
 *
 * This function renders output to the domain details interface within
 * the client area. The return should be the HTML to be output.
 *
 * @param array $params common module parameters
 *
 * @see https://developers.whmcs.com/domain-registrars/module-parameters/
 *
 * @return string HTML Output
 */
function registrarmodule_ClientArea($params)
{
    $output = <<<HTML
<div class="alert alert-info">
    Your custom HTML output goes here...
</div>
HTML;
    return $output;
}
```