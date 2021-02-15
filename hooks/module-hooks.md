+++
next = "/hooks/sample-hook"
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
Please note that hook files are detected at the time a provisioning, registrar, or addon module is activated. If a hook file is added after the module has already been activated, some additional steps may need to be performed for WHMCS to recognize it. For provisioning modules, this can be accomplished by accessing the Module Settings tab of an applicable product under **Setup** > **Products/Services** > **Products/Services** and clicking **Save Changes**. For a registrar module, re-saving the settings for it under **Setup** > **Products/Services** > **Domain Registrars** would be sufficient. Finally, for addon modules, re-saving the settings under Setup > Addon Modules will address this.
{{% /notice %}}