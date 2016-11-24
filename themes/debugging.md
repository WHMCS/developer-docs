+++
prev = "/themes/testing"
title = "Debugging"
toc = true
weight = 90

+++

Syntax errors in template files can cause a page to be unable to render completely.

Other common causes include:

* Using features of Smarty that have been removed in the upstream Smarty package
* A custom or third party module that is incompatible
* Using PHP code blocks in your template without the Allow Smarty PHP Tags setting enabled (go to Setup > General Settings > Security to enable it)

## Troubleshooting

If you see a blank page after making a change to a template file, check the **Activity Log** in <em>Utilities > Logs</em> for any logged error message.

{{% notice tip %}}
If you don't find anything in the activity logs, switching to a different template is an easy way to determine if the issue is with your template or something else.
{{% /notice %}}
