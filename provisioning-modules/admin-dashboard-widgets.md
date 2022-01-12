+++
prev = "/provisioning-modules/admin-services-tab"
next = "/provisioning-modules/module-logging"
title = "Admin Dashboard Widgets"
toc = true
weight = 100

+++

Admin Dashboard widgets display on the Admin Area homepage. They allow you to provide access to important module information and functionality on the Admin Area dashboard.

For example, the following code defines a dashboard widget:

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

For more information on the `AbstractWidget` class, see [our class documentation](http://docs.whmcs.com/classes/7.1/WHMCS/Module/AbstractWidget.html).
