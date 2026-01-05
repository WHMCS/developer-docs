+++
prev = "/themes/theme-parameters/"
next = "/themes/nexus-cart/"
title = "Order Form Templates"
toc = true
weight = 19

+++

## What is an Order Form Template?

Order Form Templates control the way products and the shopping cart appear when customers make purchases.

* You can find more information about Order Form Templates [here](https://docs.whmcs.com/Order_Form_Templates).
* You may want to refer to the [list of WHMCS-shipped Order Form Templates](https://docs.whmcs.com/Standard_Order_Form_Templates).

{{% notice tip %}}
To customise other aspects of the WHMCS Client Area, we recommend creating a [Child Theme](/themes/child-themes/).
{{% /notice %}}

{{% notice info %}}
For customization instructions specific to the Nexus Cart template, please see the [Nexus Cart](/themes/nexus-cart/) page.
{{% /notice %}}

You can set the system default Order Form Template at **Configuration > System Settings > General Settings** in the **Ordering** tab. This is where errors will display if there's a compatibility issue between the current **System Theme** and the default Order Form Template.

## Order Form Template Dependencies

An inheritance system allows parent-child relationships, with parents providing assets to children. Many custom Order Form Templates will require one or more assets in order to function. These needs are stated in the `dependencies` list in the child's `theme.yaml` file, and then are fulfilled by the items in the `provides` list in the parent's `theme.yaml` file.

{{% notice tip %}}
For more about the `theme.yaml` file and how to use it to declare and fulfill dependencies, see [The Theme Configuration File](/themes/theme-parameters/).
{{% /notice %}}

## Creating an Order Form Template

Using parent-child relationships, you don't need to create a custom copy of all of the template files. Only copy or create the files you want to customise, and the remaining Order Form Templates will then load from the parent when you define them. This will make your customised Order Form Template easier to maintain. When you upgrade to a new version of WHMCS, the system updates any changes to Order Form Template files that aren't customised.

To create an Order Form Template:

### 1. Create an Order Form Template Folder

First, create a new folder in the `/templates/orderforms/` directory.

The new directory needs a name. For example, `mycart`.

{{% notice tip %}}
Names should only contain lowercase letters, numbers, hyphens, and underscores. They cannot include spaces.
{{% /notice %}}

### 2. Create a theme.yaml File

In the new folder, create a `theme.yaml` file and populate it with information, making sure to specify a parent. At minimum, your `theme.yaml` file must contain these lines:

```
config:
  parent: standard_cart
```

{{% notice tip %}}
For more about the `theme.yaml` file and its contents, see [The Theme Configuration File](/themes/theme-parameters/).
{{% /notice %}}

### 3. Customize Files

Copy the files that you want to customise from the parent Order Form Template.

For example, the Standard Cart Order Form Template is the parent for the Premium Comparison Order Form Template. Premium Comparison consists only of a `products.tpl` Order Form Template file. All of the other steps of the order process use Standard Cart.

For a current list of Order Form Template files, see [Order Form Templates](https://docs.whmcs.com/Order_Form_Templates).

## Testing Order Form Templates

WHMCS allows you to preview Order Form Templates before making them live. This is done using the `?carttpl=xxxx` URL parameter.

## Activating Order Form Templates

You can set the Order Form Template for specific product groups at **Configuration > System Settings > Products/Services**.
