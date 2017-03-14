+++
prev = "/provisioning-modules/custom-functions"
next = "/provisioning-modules/admin-services-tab"
title = "Client Area Output"
toc = true
weight = 80

+++

Another key function of a module is to give clients access to extra options and output within the client area. Done either on the product details page (using the ClientArea function of a module), or as a [custom function/action][custom-function].

## Product Details Page Output <a id="product-details-output"></a>

Creating output to display on the same page as the product details in the client area is easy.
Create a template file named “clientarea.tpl” within the module folder.
This template file will process as a Smarty template file.
This means it can make use of Smarty variables.
The variables will be the same module vars as passed to every module function.
Also, other smarty functions such as logic functions are available.

More advanced actions, such as performing API Calls or defining variables for the output are possible.
A ClientArea function within the module that runs any code and returns an array with the template file to use, and any variables desired besides the defaults.
Returning different template file values based on data in the $_GET or $_POST array data, allows for many pages which can have direct links.

```
function mymodule_ClientArea($vars) {
    return array(
        'templatefile' => 'clientarea',
        'vars' => array(
            'test1' => 'hello',
            'test2' => 'world',
        ),
    );
}
```

## Custom Pages <a id="custom-pages"></a>

Situations that need a custom page, rather than output on the existing product details page, are possible.
Done using [custom functions][custom-function] as described earlier, with that function returning an array as follows:

```
function mymodule_mycustomfunction($vars) {
    return array(
        'templatefile' => 'customfunc',
        'breadcrumb' => array(
            'stepurl.php?action=this&var=that' => 'Custom Function',
        ),
        'vars' => array(
            'test1' => 'hello',
            'test2' => 'world',
        ),
    );
}
```

Clients then need access to use this function, and a link in the product details page.
Do this using the methods described in the previous '[Custom Functions][custom-function]' section.

[custom-function]: /provisioning-modules/custom-functions#example-function "Custom Function Example"
