+++
prev = "/themes/testing/"
next = "/themes/smarty/"
title = "Debugging"
toc = true
weight = 90

+++

## Causes of Errors

The most common error in custom system theme and order form template development, syntax errors in template files, can cause a page to be unable to render completely.

Other causes of errors include:

* Using features of Smarty that have been removed in the upstream Smarty package.
* An incompatible custom or third-party module.
* Using PHP code blocks without the **Allow Smarty PHP Tags** setting enabled at **Configuration > System Settings > General Settings** in the **Security** tab.

## Troubleshooting

If you see a blank page after making a change to a template file, check for any logged error messages in the **Activity Log** at **Configuration > System Logs**.

{{% notice tip %}}
If you don't find anything in the activity logs, switching to a different system theme or order form template is an easy way to determine if the issue is with your system theme or order form template, or if the problem is something else.
{{% /notice %}}

If you find a variable is not correctly being populated and displayed within a template, this may indicate the variable does not exist or is not available within the template it is being utilised in. Adding `{debug}` to the template file and accessing the page that calls that template in a browser will result in a popup list of all available variables within that template, allowing you to determine if that variable is available.

{{% notice tip %}}
For a full list of all template variables made available to all system themes and order form templates, see [Variables](/themes/variables/).
{{% /notice %}}