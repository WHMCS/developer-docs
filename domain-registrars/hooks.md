+++
next = "/next/path"
prev = "/prev/path"
title = "Hooks"
weight = 80

+++

Registrar modules can also define hook functions.

{{% notice info %}}
Hooks allow you to integrate with events and actions that occur inside WHMCS.
{{% /notice %}}

Hooks for your registrar module should be defined in a file named `hooks.php` within your registrar module directory.  These hooks will then be auto-detected and loaded throughout WHMCS.

The hook functions within that file should be defined in exactly the same way as normal.

Please refer to Hook Documentation for more info on creating and working with hooks in WHMCS.

