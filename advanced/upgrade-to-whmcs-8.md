+++
prev = "/intro"
title = "Upgrade to WHMCS 8.0"
toc = true
weight = 6

+++

There are several changes in WHMCS v8.0 and its dependencies that may affect third-party code.

* For your own code, you will need to manually verify this.
* For any code that comes from third-party vendors, check with the vendor to ensure it's compatible with WHMCS v8.0.

## PHP 7.2 requirement

WHMCS v8.0 and its dependencies require PHP 7.2. This may require the presence of the PHP 7.2 syntax in your code in order to avoid errors. We recommend that you consult [the PHP manual's PHP 7.2 Migration Guide](https://www.php.net/manual/en/migration72.php) as you evaluate and update your code for compatibility with WHMCS v8.0.

## Removed templates

We have removed the *Boxes* and *Modern* templates. WHMCS no longer ships with them, and we do not support them.

Make sure to update any custom order forms based on these to use the *Standard* template. You can also use the *Legacy Boxes* and *Legacy Modern* child templates as a baseline for custom templates.

Other custom templates will not be affected by this change.

## Updates for dependencies

We updated several dependencies within WHMCS while preparing for this upgrade. When ensuring that your code is compatible with WHMCS v8.0, you will likely need to update dependencies as well. The list below includes a selection of our most important updates and notes on selected changes that impacted WHMCS's code.

**Note:** You **must** independently verify whether your code and its dependencies necessitate upgrades. The updates below are highlights of WHMCS's changes, and are not comprehensive. Your code will have its own unique needs, but many of these items are likely to apply too.

### Carbon

Carbon has been upgraded from version 1 to version 2. `Carbon\Carbon::parse()` now returns false for invalid values. Previous versions of Carbon would throw an exception.

### Guzzle

Guzzle has been upgraded from version 5 to version 7. The major changes in this upgrade are listed below. For more information and a full list of changes, see [Guzzle's documentation](https://github.com/guzzle/guzzle/blob/master/UPGRADING.md).

The `client::get()` returns have changed, so you may need to switch to `getBody()->getContents` or cast `->getBody()` to a string.

You may need to consider making these changes:

* Use `base_uri` rather than `base_url`.
* Store cookies in `CookieJarInterface`, not a `key => value` array.
* When you instantiate the Guzzle Client class, move every option from the `defaults` array key to the top level of options:

```
             $client = new Client([
-                 'defaults' => [
-                    'verify' => true,
-                    'exceptions' => true,
-                    'timeout' => 10,
-                ]
+                'verify' => true,
+                'http_errors' => true,
+                'timeout' => 10,
             ]);
```

Some items have been removed:

* `CompleteEvent` is no longer defined.
* `StreamHandler` is no longer defined.
* `GuzzleHttp\Message\ResponseInterface` is no longer defined. We recommend that you replace it with `Psr\Http\Message\ResponseInterface`.

### Laravel

Capsule `pluck()` and `get()` now return a Collection rather than an array. If you'd like to minimize changes to your codebase, call `->all()` on it when you feed results into `in_array()` and similar methods. Do not call `toArray()` instead without changing consuming code. `toArray()` will convert all collection items into arrays as well (which Capsule did not do previously).

Some items are removed:

* `Builder::lists()` is removed. In most cases, we replaced this with `pluck()`.
* String helpers no longer exist, and you must replace them. For example, replace `snake_case()` with `Str::of('<string>')->snake()`.

These changes are particularly important if you use Eloquent.

### Smarty

We upgraded `smarty/smarty` from version 3.1.33 to 3.1.36. Additionally, there are changes in the use of Smarty's Security Policy parameters. For more information, see [Smarty Security Policy](https://docs.whmcs.com/Smarty_Security_Policy).

### Other

We added and updated the following additional dependencies for Composer:

| Dependency                    	| From version 	| To version 	|
|-------------------------------	|--------------	|------------	|
| `abraham/twitteroauth`         	| 0.7.4        	| 1.1.0     	|
| `composer/composer`           	| 1.0.3       	| 1.10.6     	|
| `ezyang/htmlpurifier`         	| 4.9.2        	| 4.12.0     	|
| `filp/whoops`                  	| 2.1.8        	| 2.7.2     	|
| `firebase/php-jwt`            	| 3.0.0        	| 5.2.0     	|
| `google/apiclient`            	| v2.1.3        | 2.7.0     	|
| `google/auth`                 	| 0.9.0       	| 1.11.0     	|
| `guzzlehttp/guzzle`            	| 5.3.3       	| 7.0.1     	|
| `illuminate/console`          	| 5.2.37       	| 7.12.0     	|
| `illuminate/container`         	| 5.2.37       	| 7.12.0     	|
| `illuminate/contracts`         	| 5.2.45       	| 7.12.0     	|
| `illuminate/database`         	| 5.2.37       	| 7.12.0     	|
| `illuminate/events`           	| 5.2.37       	| 7.12.0     	|
| `illuminate/support`          	| 5.2.37      	| 7.12.0     	|
| `illuminate/validation`        	| 5.2.45       	| 7.12.0     	|
| `knplabs/knp-menu`            	| 2.1.1        	| 3.1.1     	|
| `laminas/laminas-diactoros`    	| N/A         	| 2.3.1     	|
| `laminas/laminas-httphandlerrunner` 	| N/A    	| 1.2.0     	|
| `league/climate`              	| 3.2.1        	| 3.5.2     	|
| `league/flysystem`            	| 1.0.45       	| 1.0.67     	|
| `league/oauth2-client`        	| N/A         	| 2.5.0     	|
| `league/oauth2-google`        	| N/A         	| 3.0.3     	|
| `monolog/monolog`             	| 1.18.2       	| 2.0.2     	|
| `nikic/fast-route`            	| 1.2.0        	| 1.3.0     	|
| `php-imap/php-imap`           	| 2.0.9        	| 3.1.0     	|
| `phpmyadmin/sql-parser`        	| 4.2.4        	| 5.3.1     	|
| `phpmyadmin/phpmailer`         	| 6.0.7        	| 6.1.5     	|
| `phpseclib/mcrypt_compat`      	| 1.0.5        	| 1.0.11     	|
| `phpseclib/phpseclib`         	| 2.0.10       	| 2.0.27     	|
| `punic/punic`                  	| 1.6.3        	| 3.5.1     	|
| `ramsey/uuid`                 	| 3.4.1        	| 4.0.1     	|
| `react/promise`               	| 2.5.1        	| 2.8.0     	|
| `seld/jsonlint`               	| 1.6.1        	| 1.8.0     	|
| `seld/phar-utils`             	| 1.0.1        	| 1.1.0     	|
| `stripe/stripe-php`           	| 6.43.1       	| 7.34.0     	|
| `symfony/polyfill-ctype`       	| N/A         	| 1.18.1     	|
| `symfony/polyfill-iconv`       	| 1.15.0       	| 1.18.1     	|		
| `symfony/polyfill-intl-idn`    	| N/A         	| 1.18.1     	|		
| `symfony/polyfill-mbstring`    	| 1.14.0       	| 1.18.1     	|		
| `symfony/polyfill-php72`       	| N/A         	| 1.18.1     	|		
| `symfony/polyfill-php73`       	| N/A         	| 1.18.1    	|
| `tecnickcom/tcpdf`            	| 6.2.26      	| 6.3.5     	|		
| `zbateson/stream-decorators`  	| N/A         	| 1.0.3      	|	
