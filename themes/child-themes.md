+++
next = "/themes/theme-parameters"
prev = "/themes/getting-started"
title = "Child Themes"
toc = true
weight = 15

+++

## What is a Child Theme?

A Child Theme is a theme that inherits templates and assets from another theme, referred to as the Parent Theme.

With a Child Theme, your theme only needs to contain the templates you wish to customise and change. For CSS/styling only customisations, your theme doesn't have to contain any template files at all.

The result is a smaller theme that's easier to maintain, and that automatically receives updates to template files which are not customised, making applying software updates faster, easier and more automated.

A Child Theme is the recommended way to customise WHMCS as of WHMCS 8.

## Why use a Child Theme?

1. Separation of Customisations - A child theme can be used to make modifications to any part of a theme in a way that keeps those customisations separate from the Parent Theme's files.
2. Simplified Maintenance/Updates - Using a Child theme has the benefit of referencing all non-customised files from the Parent Theme, making updates easier by having changes in the parent theme automatically take effect within the Child Theme.

## What is a Parent Theme?

A parent theme is a complete theme which includes all of the required WHMCS template files and assets for the theme to work.

The `Six` and `Twenty-One` themes that ship by default with WHMCS are both Parent Theme's.

## Geting Started

### 1. Create a Child Theme folder

First, create a new folder in the `templates` directory.

The directory needs a name. For example, `mytheme`.

{{% notice tip %}}
Theme directory names should be a single word, consisting of only lowercase letters and numbers, hyphens and underscores.
{{% /notice %}}

### 2. Create a theme.yaml file

Next, you'll need to create a theme.yaml file which tells WHMCS this is a Child Theme, and defines the Parent Theme to be used.

The sample below defines a name, author and parent theme of "twenty-one".

```
# My Theme Configuration File

name: "My Custom Theme"
author: "WHMCS Limited"
config:
  parent: twenty-one
```

The following information is required:

Name - this is the name you will see displayed in the WHMCS admin interface
Author - this should be your name
Config / Parent - the name of the parent theme directory. The parent theme in our example is the Twenty-One theme, so the parent theme directory name is "twenty-one".

The theme.yaml file can also define other parameters about your theme. To learn more, see [Theme Parameters](/themes/theme-parameters/).

### 3. Create a custom.css file

Next, create a sub-folder named `css`, and within that, create a stylesheet file named `custom.css`.

This is where you should put the CSS rules and declarations to control the look of your theme. Anything you define here will override styling defined by the Parent Theme.

```
// Example override for the primary background color
.primary-bg-color {
    background-color: #ddd;
}
```

{{% notice info %}}
The custom.css stylesheet will be loaded automatically providing the Parent Theme supports it. All themes that ship by default with WHMCS offer this functionality.
{{% /notice %}}

### 4. Preview the theme

To preview the theme, you can use the `?systpl=xxxx` url parameter.

To learn more, see [Testing](/themes/testing/).

### 5. Activate the theme

Once you’re happy with your new theme and are ready to make it live, follow the steps below:

1. Login to your WHMCS Admin Area
2. Navigate to *Configuration > System Settings > General Settings*
3. Under the **System Theme** setting on the *General tab*, select the name of the theme you created above
4. Hit **Save Changes** and visitors to your site will immediately begin seeing your new theme


## Adding Template Files

Any file you add to your Child Theme will override the same file in the Parent Theme.

Commonly overriden files include the header and footer template files, along with pages such as the homepage, client area home and contact pages.

{{% notice tip %}}
In most cases, it is usually best to create a copy of the template file(s) you want to customise from the Parent Theme, then make your modifications to the copied files, leaving the parent files unchanged.
{{% /notice %}}

For example, if you wanted to change the code of the Parent Theme's header.tpl file, you would copy the file to your Child Theme folder and customise it there.

{{% notice info %}}
This is particularly important for files such as the header and footer, which contain important and essential code required for the correct and normal operation of the WHMCS client area.
{{% /notice %}}


## Loading Assets

The `assetPath` helper is available for use in themes to load assets in a smart way and enable Child Themes to override them.

Use of this function is particularly important for Parent Theme developers to make it possible for Child Theme developers to override assets without editing file paths. However in most Child Themes, assets may be loaded in the normal way - with hardcoded paths - without any negative side effects.

Example usage of the `assetPath` helper:

```
<link href="{assetPath file='mycssfile.css'}" rel="stylesheet">
<script src="{assetPath file='myjsfile.js'}"></script>
```

To learn more about the assetPath helper and other functions available to Theme Developers, see [Functions](/themes/functions/)
