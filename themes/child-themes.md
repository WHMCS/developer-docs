+++
next = "/themes/theme-parameters"
prev = "/themes/getting-started"
title = "Child Themes"
toc = true
weight = 15

+++

## What is a Child Theme?

A Child Theme is a theme that inherits templates and assets from another theme, referred to as the Parent Theme.

With a Child Theme, your theme only needs to contain the template files you wish to customise and change. For CSS styling-only customisations, your theme doesn't have to contain any template files at all.

The result is a smaller theme that's easier to maintain, and that automatically receives updates to template files that are not customised, making applying software updates faster, easier, and more automated.

A Child Theme is the recommended way to customise WHMCS as of WHMCS 8.

### Why Use a Child Theme?

There are two main reasons to use Child Themes:

1. Separation of Customisations — A Child Theme can be used to customise any part of a parent theme in a way that keeps those customisations separate from the Parent Theme's files.
2. Simplified Maintenance and Updates — Using a Child Theme has the benefit of referencing all uncustomised files from the Parent Theme. This makes updates easier by having changes in the Parent Theme automatically take effect within the Child Theme.

## What is a Parent Theme?

A parent theme is a complete theme that includes all of the WHMCS template files and assets that the theme requires in order to work.

The `Twenty-One`, `Nexus`, and `Six` themes that ship by default with WHMCS are Parent Themes.

## Getting Started

You can use these steps to create a Child Theme:

### 1. Create a Child Theme Folder

First, create a new folder in the `templates` directory.

The new directory needs a name. For example, `mytheme`.

{{% notice tip %}}
Names should only contain lowercase letters, numbers, hyphens, and underscores. They cannot include spaces.
{{% /notice %}}

### 2. Create a theme.yaml File

Next, you'll need to create a `theme.yaml` file to indicate to WHMCS that this is a Child Theme. It must define the Parent Theme to be used.

The sample below defines a name, author, and parent theme (`twenty-one`).

```
# My Theme Configuration File

name: "My Custom Theme"
author: "WHMCS Limited"
config:
  parent: twenty-one
```

The following information is required:

* `name` — The name you will see in the WHMCS Admin Area.
* `config` / `parent` — The name of the Parent Theme directory. The Parent Theme in the example above is the Twenty-One theme, so the parent theme directory name is `twenty-one`.

The `theme.yaml` file can also define other parameters about your theme. To learn more, see [Theme Parameters](/themes/theme-parameters/).

You can create child themes with parents that are, in turn, children of other themes, as long as the ultimate parent theme includes all of the required WHMCS template files and assets. However, we do not recommend this for most uses.

### 3. Create a custom.css File

{{% notice info %}}
If you do not intend to make *any* CSS-related changes you can skip this step. However, we strongly recommend doing this for all new Child Themes.
{{% /notice %}}

Create a subfolder named `css`, and, within that, create a stylesheet file named `custom.css`.

This is where you should put the CSS rules and declarations to control the look of your theme. Anything you define here will override styling defined by the Parent Theme. If you only want your Child Theme to contain CSS updates, using this method will give you a maintenance-free, automatically-updating Child Theme.

```
/* Example override for the primary background color */
.primary-bg-color {
    background-color: #ddd;
}
```

{{% notice info %}}
The `custom.css` stylesheet will be loaded automatically if the Parent Theme supports it. All themes that ship by default with WHMCS offer this functionality.
{{% /notice %}}

### 4. Update Files

{{% notice info %}}
If you are **only** making CSS customisations (via the `css/custom.css` file above), you can skip this step.
{{% /notice %}}

If you are customising files that exist in the Parent Theme, we recommend copying those files to your theme folder and then customising them as needed. Leave the Parent Theme's copy of the file unchanged.

Any file you add to your Child Theme will override the same file in the Parent Theme. Commonly-overridden files include the header and footer template files, the homepage, client area home, and contact pages. For example, to customise the footer, you would copy the Parent Theme's `footer.tpl` file to the Child Theme's folder and customise it there.

{{% notice info %}}
Copying the file's contents and customising it rather than starting from an empty file is particularly important for customising the header and footer, which contain essential code required for the correct operation of the WHMCS Client Area.
{{% /notice %}}

You can also incorporate your own newly-created files for use in your customisations.

### 5. Preview the Theme

To preview the theme, you can use the `?systpl=xxxx` URL parameter.

To learn more, see [Testing](/themes/testing/).

### 6. Activate the Theme

Once you're happy with your new theme and are ready to make it live, follow the steps below:

1. Log in to your WHMCS Admin Area.
2. Navigate to **Configuration > System Settings > General Settings**.
3. Under the **System Theme** setting on the **General** tab, select the name of the theme you created above.
4. Click **Save Changes** and visitors to your site will immediately begin seeing your new theme.

## Loading Assets

The `assetPath` helper is available for use in themes. It loads assets in a smart way and enables Child Themes to override them.

Use of this function is particularly important for Parent Theme developers. It makes it possible for Child Theme developers to override assets without editing file paths. However, in most Child Themes, assets may be loaded in the normal way — with hardcoded paths — without any negative side effects.

Example usage of the `assetPath` helper:

```
<link href="{assetPath file='mycssfile.css'}" rel="stylesheet">
<script src="{assetPath file='myjsfile.js'}"></script>
```

To learn more about the `assetPath` helper and other functions available to Theme Developers, see [Functions](/themes/functions/)
