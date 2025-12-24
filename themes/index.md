+++
chapter = true
icon = "<i class='fa fa-paint-brush fa-fw'></i>"
next = "/themes/getting-started"
title = "Themes"
weight = 0

+++

## Introduction

System themes and order form templates let you control the Client Area, the client-facing user interface in WHMCS. WHMCS allows you to provide a seamless experience for your customers by customising the look of the Client Area to match your company's website and branding.

## System Themes

Themes, or *System Themes*, in WHMCS control the client-facing user interface. WHMCS allows you to provide a seamless experience for your website visitors by using system themes to customise the Client Area to match the rest of your website.

WHMCS currently ships with three system themes for the Client Area:

* **Nexus** was introduced in WHMCS 9.0.
* **Twenty-One** was introduced in WHMCS 8.1 and is currently the default system theme for new installations.
* **Six** was the default theme for WHMCS 6.0 through 8.0.

We recommend using and customising **Twenty-One** or **Nexus**. We will remove **Six** in a future version of WHMCS.

{{% notice tip %}}
We recommend using [Child Themes](/themes/child-themes/) for your customisations.
{{% /notice %}}

You can set the **System Theme** in WHMCS's Admin Area at **Configuration > System Settings > General Settings** in the **General** tab.

## Order Form Templates

Order form templates control the look and feel of individual product and shopping cart pages in the Client Area.

You can set a **Default Order Form Template** at **Configuration > System Settings > General Settings** in the **Ordering** tab. You can also select an order form template for individual product groups at **Configuration > System Settings > Products/Services**.

In WHMCS 8.1 and later, WHMCS automatically checks for compatibility between your **System Theme** and the order form templates you use.

For more information about order form templates, see [Order Form Templates](/themes/order-form-templates/).
