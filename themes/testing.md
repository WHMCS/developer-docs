+++
next = "/themes/debugging/"
prev = "/themes/php/"
title = "Testing"
toc = true
weight = 80

+++

WHMCS allows you to preview a template before making it live.

This is done using the `?systpl=xxxx` url parameter.

For example, if your new theme was named 'mytemplate' and your WHMCS client area was located at http://www.yourdomain.com/whmcs/, you would navigate to:

> http://www.yourdomain.com/whmcs/?systpl=mytemplate

The template will be stored for the duration of your browser session allowing you to exercise all areas of the client area with your new theme.

## Making your template live

Once you're happy with your new template and are ready to make it live, follow the steps below:

1. Login to the Admin Area
2. Navigate to <em>Setup > General Settings</em>
3. Under the Template setting on the General tab, select the name of the template you created above
4. Hit **Save Changes** and visitors to your site will immediately begin seeing your new template
