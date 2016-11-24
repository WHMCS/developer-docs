+++
next = "/languages/contributing/"
prev = "/languages/overrides/"
title = "Translating"
weight = 50

+++

In addition to regular words and phrases, language file strings may also use the following constructs within them:

* Using named tags, like `:page`
* Using variable names, like `$price`
* Using `%s` for string replacements

In the first two examples, WHMCS will substitute them into the final output for the string at the time it is used, so it is important to keep them intact and untranslated in your translations. So `:page` will always be page, and `$price` will always be $price.

For the string replacement `%s` type, the number and order of `%s` should not be changed as the product will replace the `%s` values in order from beginning to end.

## Examples

```
$_LANG['examplestring'] = "The price you will pay today is :price";
```

Correct Translation = " 'ay' yIbuS DaHjaj :price "
Incorrect Translation = " 'ay' yIbuS DaHjaj :'ay' "

This would display :'ay' instead of the price on the translated page.

```
$_LANG['examplestring'] = "Today is a good day to purchase your domain $domain for cheap!";
```

Correct Translation = " DaHjaj QaQ jaj yer $domain je' qutlh! "
Incorrect Translation = " DaHjaj QaQ jaj yer $yer je' qutlh! "

This would display everything but $yer: "DaHjaj QaQ jaj yer je' qutlh!"

```
$_LANG['examplestring'] = "Honor your house with a server for only %s a year! (%s a month)
```

Correct Translation = "tuqwIj neH %s jabwI' pop! (%s net jar)"
Incorrect Translation 1 = "tuqwIj je jabwI' pop! (%s net jar pagh %s)"
Incorrect Translation 2 = "tuqwIj %s net jar jabwI' pop!"

In the first wrong translation, "net jar pagh" means "X a month, or Y a year". Because WHMCS will be replacing these in the original order, you'll end up showing the prices backwards.

In the second wrong translation, we removed the part talking about the yearly price and only mention the monthly price. However, WHMCS will still replace the first %s it sees with the yearly price, so you'll end up quoting the yearly price as monthly.
