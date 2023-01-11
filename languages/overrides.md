+++
next = "/languages/translating/"
prev = "/languages/encoding/"
title = "Overrides"
weight = 40

+++

The language files are provided unencoded to allow you to view the language strings that WHMCS uses.

However we do not recommend editing these files directly. Instead overrides should be used.

Language file overrides allow you to customise language strings and phrases in a way that is safely preserved through the upgrade process.

## Using Overrides

Steps for customising language strings via overrides are as follows:

1. Create a directory named `overrides` within the `/path/to/whmcs/lang/` directory.
2. Create or copy the language file you want to override. For example, to create an override for the English language you create `/path/to/whmcs/lang/overrides/english.php`
3. Open the newly created file in your preferred editor.
4. Start the file with a PHP tag `<?php` indicating PHP code is to be used.
5. Enter the variable(s) you wish to override. For example, if you wanted to change "Welcome to our members area" you would locate the proper variable within `/path/to/whmcs/lang/english.php` and place it into the overrides english file with your preferred change:

`/path/to/whmcs/lang/english.php`
```
$_LANG['headertext'] = "Welcome to our members area.";
```

`/path/to/whmcs/lang/overrides/english.php`
```
$_LANG['headertext'] = "Welcome home!";
```

6. For each variable you wish you change, repeat step #5. For example, a completed overrides file should look something like this:

`/path/to/whmcs/lang/overrides/english.php`
```
<?php
$_LANG['headertext'] = "Welcome home!";
$_LANG['addtocart'] = "Add to Basket";
$_LANG['cartproductaddons'] = "Product Extras";
```

7. Save, and you're done!
