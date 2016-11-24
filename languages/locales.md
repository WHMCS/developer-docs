+++
next = "/languages/encoding/"
prev = "/languages/adding-a-language/"
title = "Locales"
weight = 20

+++

Locales define the language and region for a language file.

Each language file in WHMCS requires a locale to be defined in the following format:

```
$_LANG['locale'] = "en_GB";
```

The above defines that the language is English (en), and the region is Great Britain (GB).

The locale information is used by WHMCS to localise and display the language name localised to the native language within the WHMCS client area.

Failure to provide a valid locale will prevent the language file from showing up as available for use within WHMCS.
