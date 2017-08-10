+++
next = "/modules/marketplace/"
prev = "/modules/code-samples/"
title = "Style Guide"
weight = 30

+++

The following describes the recommended programming style and best practices when developing with WHMCS.

## PHP Code Tags

Always use `<?php ?>` to delimit PHP code, not the shorthand, `<? ?>`. This is the most portable format to ensure compatibility for differing operating systems and set-ups.

If a file is pure PHP code, it is preferable to omit the PHP closing tag at the end of the file. This prevents accidental whitespace or new lines being added after the PHP closing tag which may cause unwanted side effects including "header already sent" errors, XHTML/XML validation issues, and other problems.

## Indenting and whitespace

Use an indent of 4 spaces, with no tabs.

Lines should have no trailing whitespace at the end.

Files should be formatted with `\n` as the line ending (Unix line endings), not `\r\n` (Windows line endings).

All files should end in a single newline (\n). This avoids the verbose "\ No newline at end of file" warning and makes it clearer what is being changed when lines are added to the end of a file.

## PSR Coding Standards

The PHP Standard Recommendation (PSR) is a PHP specification published by the PHP Framework Interop Group. It comprises what should be considered the standard coding elements that are required to ensure a high level of technical interoperability between shared PHP code.

At WHMCS we follow the `PSR-1` and `PSR-2` standards for all code we create, and we strongly recommend you do the same:

* Basic Coding Standard: http://www.php-fig.org/psr/psr-1/
* Coding Style Guide: http://www.php-fig.org/psr/psr-2/

## Character Encoding

All PHP files should be encoded using `UTF-8 without BOM` (no byte-order-mark).
