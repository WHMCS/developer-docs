+++
prev = "/themes/child-themes/"
next = "/themes/order-form-templates/"
title = "The Theme Configuration File"
toc = true
weight = 18

+++

## The theme.yaml File

Parent Themes, [Child Themes](/themes/child-themes/), and Order Form Templates should include a `theme.yaml` file. This file defines the theme or Order Form Template, including its name and author, description, its parent, its dependencies, and the assets it can provide for any children to which it is the parent.

{{% notice tip %}}
We made this method available for Order Form Templates in WHMCS 6.1 and improved it to include themes in WHMCS 8.1.
{{% /notice %}}

For example, this `theme.yaml` file sets the theme as a child of the Twenty-One Parent Theme, as well as specifying other theme information:

```
name: "Example"
description: "My Company's Branding"
author: "Hosting Company, L.L.C."
config:
  parent: twenty-one
dependencies:
  bootstrap: 4.5.2
provides:
  jquery: 1.12
  fontawesome: 5
```

This file **must** be a valid [YAML file](https://en.wikipedia.org/wiki/YAML) and must use the indentation style illustrated above.

## Parameters

You can specify these items in a `theme.yaml` file:

### name

The System Theme or Order Form Template name.
* For System Themes, this displays in the **System Theme** menu at **Configuration > System Settings > General Settings** in the **General** tab.
* For Order Form Templates, this displays in **Configuration > System Settings > General Settings** in the **Ordering** tab and for individual product groups at **Configuration > System Settings > Products/Services**.

### description

A description of the theme or Order Form Template.

### author

Generally, this should be your name. It could also be your company's name.

### config: parent

The name of the directory that contains the Parent Theme or Order Form Template. (Do not use the display name.)

### dependencies

{{% notice tip %}}
It is unlikely for a theme to list anything under `dependencies`.
{{% /notice %}}

A list of assets that a child needs its parent to provide in order to function. If you don't specify anything under `dependencies`, WHMCS assumes compatibility. (This behavior is necessary in order to ensure continued compatibility with older custom themes.)

### provides

A list of assets that the theme or Order Form Template can provide to any children.

## Compatibility

WHMCS checks for compatibility between themes and Order Form Templates each time that you select a theme from the **System Theme** menu at **Configuration > System Settings > General Settings** in the **General** tab. This checks the `provides` list, `dependencies` list, and `config` details in order to make this assessment.

{{% notice tip %}}
If you receive an error, start troubleshooting by checking the `theme.yaml` files for both the theme (and its parents) and the Order Form Template (and its parents). This will allow you to identify which dependencies aren't being met.
{{% /notice %}}

When checking `provides` and `dependencies` lists, WHMCS assumes compatibility for any missing segments of the version number. For example, if you set an Order Form Template to have Bootstrap 4 as a dependency in the `dependencies` list, WHMCS will consider Bootstrap 4.5.2 (or any other version number beginning in `4.`) as fulfilling it in the `provides` list for the Parent Theme.
