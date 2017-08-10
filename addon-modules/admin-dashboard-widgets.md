+++
next = "/addon-modules/upgrades"
prev = "/addon-modules/hooks"
title = "Admin Dashboard Widgets"
toc = true
weight = 80

+++

Admin Dashboard Widgets are displayed on the admin area homepage.

They allow you to provide convenient access to key information and functionality from your module within the admin homepage dashboard.

Below is an example of how a dashboard widget is defined.

```
<?php

add_hook('AdminHomeWidgets', 1, function() {
    return new HelloWorldWidget();
});

/**
 * Hello World Widget.
 */
class HelloWorldWidget extends \WHMCS\Module\AbstractWidget
{
    protected $title = 'Hello World';
    protected $description = '';
    protected $weight = 150;
    protected $columns = 1;
    protected $cache = false;
    protected $cacheExpiry = 120;
    protected $requiredPermission = '';

    public function getData()
    {
        return array();
    }

    public function generateOutput($data)
    {
        return <<<EOF
<div class="widget-content-padded">
    Hello World!
</div>
EOF;
    }
}
```

More information on the AbstractWidget class used in the above example can be found at http://docs.whmcs.com/classes/7.1/WHMCS/Module/AbstractWidget.html
