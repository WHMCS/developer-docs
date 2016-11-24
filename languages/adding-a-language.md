+++
next = "/languages/locales/"
prev = "/languages/"
title = "Adding a Language"
weight = 10

+++

The language system in WHMCS allows you to create your own additional language translations.

We recommend starting by duplicating one of the existing language files.

{{% notice info %}}
Language file names should be a single word, consisting of only lowercase letters and numbers. The file must end with the extension **.php**.
{{% /notice %}}

1. Begin by opening an existing language file, for example `lang/english.php`
2. Save this file with a new name. The name you choose will be shown in the language selection dropdown menu inside WHMCS.
3. Translate the words and phrases contained within it into your new language. Be careful not to change the language key names, only the words and phrases contained within the double quotes on each line.

{{% notice tip %}}
Be careful not to delete any of the quotation marks (") around the text strings or the semi-colons on the ends of each line (;). Also should you want to use a quote character (") within your translated text, you must escape it - for example: \" The language files are written in PHP syntax so valid PHP code must be maintained.
{{% /notice %}}

4. Upload your new language file to your WHMCS installations `/lang/` directory.
5. The language file will now be available for use.

Test it by visiting your WHMCS installation client area and selecting the language file from the dropdown. If you encounter any errors, this suggests your changes to the language file have introduced a syntax error. Please double check your modifications and try again.
