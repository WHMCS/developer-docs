+++
next = "/hooks/priority"
prev = "/hooks/index"
title = "Getting Started"
toc = true
weight = 5

+++

The following steps demonstrate how to create a hook function in WHMCS.

## Create your Hook File

Hooks in WHMCS exist in the `/includes/hooks/` directory. Alternately, they may be within a module (for more information, see [Module Hooks](/hooks/module-hooks/)).

The example process below creates a WHMCS hook.

## 1. Create the Hook File

Create the `helloworld.php` file in the `/includes/hooks/` directory:

```
touch ~/includes/hooks/helloworld.php
```
To exclude a hook file from execution, prefix the filename with an underscore (`_`).

## 2. Add the Hook Function

Add the hook code to the new `.php` file. Hook functions can be either named functions or closures.

* For an example of hook code, see [Sample Hook](/hooks/sample-hook).
* Hook functions can be either named functions or closures.

When the hook code runs, the system will pass a selection of variables to your hook point. The variables you receive will depend on the invoked action and the data that is available to it.

Some hook points will also allow you to return values. In some cases, the response you provide can override default behaviours.

{{% notice info %}}
When using a named function, prefix your function name with something unique to you and your code in order to prevent naming conflicts.
{{% /notice %}}
