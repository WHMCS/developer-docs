+++
next = "/themes/child-themes"
prev = "/themes/index"
title = "Getting Started"
toc = true
weight = 10

+++

The default theme that ships with WHMCS is called the **Twenty-One** theme.

If you wish to customise any of the themes that ship by default with WHMCS, we recommend using the [Child Themes](/themes/child-themes) functionality.

## Creating a Child Theme

{{% notice tip %}}
Recommended for all new theme development in WHMCS 8.1 and later.
{{% /notice %}}

Please see [Child Themes](/themes/child-themes) for more information.

## Creating a Custom Theme

If you wish to create a new Parent Theme (that other themes can inherit from and be a child of), or are using an older version of WHMCS, you can create a Custom Theme. For all other scenarios, we recommend using [Child Themes](/themes/child-themes).

The first step is to create your own copy of the template. This ensures your customisations are not lost when updating.

### Method 1: Using Source Control

If you're familiar with GIT Version Control, we make the Six theme available as a read-only repository on [Github](https://github.com/WHMCS/templates-six) that enables you to build your template in a way that can be tracked and automatically updated.

To use this, navigate to the WHMCS templates directory:

```
$ cd ~/whmcs/templates/
```

Clone the Six template theme repo into your new template directory:

```
$ git clone https://github.com/WHMCS/templates-six.git my-template-name
```

Now begin making your changes

### Method 2: Non source controlled

Alternatively, if you aren't familiar with GIT Source Control or don't wish to use it, you can simply make a copy of the **Six** template directory.

1. Copy the `~/templates/six/` directory to `~/templates/yourname/`

{{% notice info %}}
Template names should be a single word, consisting of only lowercase letters and numbers.
{{% /notice %}}

Now it's time to [customise your theme](/themes/customising).
