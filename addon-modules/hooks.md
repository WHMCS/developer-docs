+++
next = "/addon-modules/admin-dashboard-widgets"
prev = "/addon-modules/multi-language"
title = "Hooks"
toc = true
weight = 70

+++

Hooks that the module should define within WHMCS are defined in a file named “hooks.php”.
This should be within your custom module folder.
That will then become detected and any hooks that exist will be loaded on every page of WHMCS.

The hook functions within that file should be defined in exactly the same way as normal.

Please refer to [Hook Documentation][hook-documentation] for more info on creating and working with hooks in WHMCS.

[hook-documentation]: https://developers.whmcs.com/hooks/ "Hooks"
