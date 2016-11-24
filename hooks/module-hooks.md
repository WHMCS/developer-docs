+++
next = "/hooks/sample"
prev = "/hooks/priority"
title = "Module Hooks"
toc = true
weight = 15

+++

Module hooks follow all the same principles as regular hooks.

## Defining Hooks within a Module

To provide hooks as part of a module, create a file named `hooks.php` in the root of your module directory.

This hooks file will be detected and loaded by WHMCS on every page load.

{{% notice note %}}
Hook files are only detected at the time a module is activated and configured. If you add your hook file after the module has already been activated, you may need to deactivate and reactivate your module in order for WHMCS to recognise it.
{{% /notice %}}
