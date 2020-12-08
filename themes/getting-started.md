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

If you wish to create a new Parent Theme (that other themes can inherit from and be a child of), or are using WHMCS 8.0 or earlier, you can create a Custom Theme. For all other scenarios, we recommend using [Child Themes](/themes/child-themes).

The first step is to create your own copy of the template. This ensures your customisations are not lost when updating.

### Method 1: Using Source Control

If you're familiar with Git version control, we make our system themes and order form templates available as read-only repositories on [GitHub](https://github.com/WHMCS/). You can use these to build your template in a way that can be tracked and automatically updated.

To use this, navigate to the WHMCS templates directory:

```
$ cd ~/whmcs/templates/
```

Then, clone the repository into your new template directory:

```
$ git clone https://github.com/WHMCS/templates-six.git my-template-name
```

Next, you can [customise](/themes/customising) your system theme or [order form template](/themes/order-form-templates).

### Method 2: Without Source Control

Alternatively, if you aren't familiar with Git version control or don't wish to use it, you can make a copy of the template directory within WHMCS.

To do this, copy the theme or order form template directory (for example, `~/templates/twenty-one/`) to `~/templates/yourname/`.

{{% notice info %}}
Template names should be a single word, consisting of only lowercase letters and numbers.
{{% /notice %}}

Next, you can [customise](/themes/customising) your system theme or [order form template](/themes/order-form-templates).
