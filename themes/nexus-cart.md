+++
prev = "/themes/order-form-templates/"
next = "/themes/customising/"
title = "Nexus Cart"
toc = true
weight = 19.5

+++

## Overview

The Nexus Cart is a modern order form template introduced in WHMCS 9.0 as part of the Nexus theme. It provides a streamlined, single-page application (SPA) experience for domain registration and shopping cart pages.

{{% notice info %}}
The Nexus Cart is designed to work seamlessly with the Nexus system theme and provides an enhanced user experience for your customers.
{{% /notice %}}

## Development Notes

### Layout Customization

The layout of Nexus SPA pages (such as the domain pricing, results, and view cart pages) cannot be modified. Customization is limited to visual styling through CSS, allowing changes to colors and formatting only.

### Theme Styles Customization

Customers can fully customize the colors and styles of the Nexus theme (regular and SPA) through the `custom.css` file by using CSS variables. This allows you to change the appearance without the need to build Sass files.

## How to Customize

To customize the Nexus Cart theme:

1. Open the file `templates/nexus/css/custom.css`.
2. Change the values of CSS variables (custom properties) to the desired colors, rounding, or other values.
3. Save the file. Changes will be applied automatically to the entire template – Client Area pages and new SPA pages (Domain Registration Page and Cart Page).

## All Possible Variables to Change

Below is the complete list of CSS variables available for customization in the Nexus theme:

```css
/* Custom CSS for Nexus Theme
 *
 * This file allows you to customize the theme colors and styles for the entire Nexus template.
 *
 * To customize colors:
 * - Replace the var() references with your own hex colors or other CSS values.
 * - For example, instead of --primary: #4b5563; use --primary: #your-color;
 * - You can also override any CSS properties here.
 */
:root {
    --white: #fff;
    /* Neutral shades */
    --neutral-50: #fbf9fa;
    --neutral-100: #f4f5f7;
    --neutral-200: #e4e4e7;
    --neutral-300: #d0d5dd;
    --neutral-400: #9ca3af;
    --neutral-500: #6b7280;
    --neutral-600: #4b5563;
    --neutral-700: #374151;
    --neutral-800: #1f2937;
    --neutral-900: #111827;
    --neutral-950: #030712;
    
    /* Primary shades */
    /* define own pallet with brand colors */
    --primary-50: var(--neutral-50);
    --primary-100: var(--neutral-100);
    --primary-200: var(--neutral-200);
    --primary-300: var(--neutral-300);
    --primary-400: var(--neutral-400);
    --primary-500: var(--neutral-500);
    --primary-600: var(--neutral-600);
    --primary-700: var(--neutral-700);
    --primary-800: var(--neutral-800);
    --primary-900: var(--neutral-900);
    --primary-950: var(--neutral-900);
    
    /* Primary colors */
    /* Use shades from comments if `primary` colors use other colors, then neutral */
    --primary: var(--neutral-900);          /* var(--primary-600) */
    --primary-lifted: var(--neutral-800);   /* var(--primary-700) */
    --primary-accented: var(--neutral-700); /* var(--primary-800) */
    
    /* Secondary colors */
    --secondary: var(--neutral-500);
    --secondary-lifted: var(--neutral-600);
    --secondary-accented: var(--neutral-700);
    
    /* Success colors */
    --success: #00a63e;
    --success-lifted: #008236;
    --success-accented: #016630;
    
    /* Info colors */
    --info: #155dfc;
    --info-lifted: #1447e6;
    --info-accented: #193cb8;
    
    /* Notice colors */
    --notice: #7f22fe;
    --notice-lifted: #7008e7;
    --notice-accented: #5d0ec0;
    
    /* Warning colors */
    --warning: #f54a00;
    --warning-lifted: #ca3500;
    --warning-accented: #9f2d00;
    
    /* Error colors */
    --error: #e7000b;
    --error-lifted: #c10007;
    --error-accented: #9f0712;
    
    /* Grayscale colors */
    --grayscale: var(--neutral-900);
    --grayscale-lifted: var(--neutral-800);
    --grayscale-accented: var(--neutral-700);
    
    /* Neutral colors */
    --neutral: var(--neutral-500);
    --neutral-lifted: var(--neutral-600);
    --neutral-accented: var(--neutral-700);
    
    /* Text neutral colors */
    --text-inverted: var(--white);
    --text-muted: var(--neutral-400);
    --text-lifted: var(--neutral-500);
    --text-accented: var(--neutral-600);
    --text: var(--neutral-900);
    
    /* Border neutral colors */
    --border-muted: var(--neutral-200);
    --border: var(--neutral-300);
    --border-lifted: var(--neutral-400);
    --border-accented: var(--neutral-600);
    
    /* Background neutral colors */
    --bg: var(--white);
    --bg-muted: var(--neutral-50);
    --bg-lifted: var(--neutral-100);
    --bg-accented: var(--neutral-200);
    --bg-inverted: var(--neutral-900);
    
    /* Additional colors */
    --yellow-200: #fff085;
    --yellow-300: #ffdf20;
    --teal-300: #46edd5;
    --teal-400: #00d5be;
    --emerald-300: #5ee9b5;
    --pink-400: #fb64b6;
    
    /* Additional custom properties */
    
    /* Font sizes */
    --text-xs: 0.625rem;
    --text-sm: 0.75rem;
    --text-md: 0.875rem;
    --text-lg: 1rem;
    
    /* Spacing */
    --outline-sm: 1px;
    --outline-md: 2px;
    --outline-lg: 3px;
    
    /* Rounding */
    --rounding-sm: 0.25rem;
    --rounding-md: 0.5rem;
    --rounding-lg: 0.75rem;
    
    /* Other */
    --letter-spacing: 0em;
    --disabled-opacity: 25%;
}
```

## Important Notes

* Changes in `custom.css` override the default values from `theme.min.css`.
* The file is loaded after the main styles, so your changes take priority.
* For the orderform (cart), colors are also applied since it uses the same variables.
* If you need to override specific elements, add CSS rules below `:root`.

