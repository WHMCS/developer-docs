+++
prev = "/themes/functions/"
next = "/themes/php/"
title = "Conditionals"
toc = true
weight = 70

+++

It is often necessary to display text or messages when certain conditions are met.

{if} statements in Smarty have much the same flexibility as PHP if statements.

Every {if} must be paired with a matching {/if}. {else} and {elseif} are also permitted.

All PHP conditionals and functions are recognized, such as `||`, `or`, `&&`, `and`, `is_array()`, etc.

## Example

```
{if $filename eq "announcements.php"}
    This is the announcements page
{else}
    This is not the announcements page
{/if}
```

For more information, please refer to http://www.smarty.net/docs/en/language.function.if.tpl
