+++
next = "/themes/customising"
prev = "/themes/index"
title = "Getting Started"
toc = true
weight = 10

+++

The default template that ships with WHMCS 6.0 and later is called the **Six** theme.

Before you begin customising it for your needs, the first step is to create your own copy of the template. This ensures your customisations are not lost when updating.

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
