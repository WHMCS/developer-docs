+++
prev = "/provisioning-modules/usage-update"
next = "/provisioning-modules/custom-functions"
title = "Usage Metrics"
toc = true
weight = 65

+++
`Compatibility: This functionality is available since v7.9`

Usage metrics give Services information about resource consumption and Products
the ability to price those resources.

Please make sure to read the feature documentation for 
[Usage Billing](https://docs.whmcs.com/Usage_Billing) so that you have the best
understanding of how your module is expected to interact with WHMCS.

## MetricProvider Function
The MetricProvider function is responsible for returning an object that implements
\WHMCS\UsageBilling\Contracts\Metrics\ProviderInterface.   

This object provides a list of available metrics, all usage of the server, and
usage by given tenant on that server.
Interface and class are documented in the WHMCS\UsageBilling namespace at https://classdocs.whmcs.com/

The following illustrates how one might make a simple class that fulfills the interface
```
namespace WHMCS\Module\Server\Mymodule;
/**
 * The above namespace is automatically registered for autoloading classes within
 * a "lib" sub-directory relative to your module directory. So, place this class 
 * in modules/servers/mymodule/lib/MyMtricsProvider.php. 
 */

use WHMCS\UsageBilling\Contracts\Metrics\MetricInterface;
use WHMCS\UsageBilling\Contracts\Metrics\ProviderInterface;
use WHMCS\UsageBilling\Metrics\Metric;
use WHMCS\UsageBilling\Metrics\Units\Accounts;
use WHMCS\UsageBilling\Metrics\Usage;

class MyMetricsProvider implements ProviderInterface
{
    private $moduleParams = [];
    public function __construct($moduleParams)
    {
        // A sample `$params` array may be defined as:
        //
        // ```
        // array(
        //     "server" => true
        //     "serverid" => 1
        //     "serverip" => "11.111.4.444"
        //     "serverhostname" => "my.testserver.tld"
        //     "serverusername" => "root"
        //     "serverpassword" => ""
        //     "serveraccesshash" => "ZZZZ1111222333444555AAAA"
        //     "serversecure" => true
        //     "serverhttpprefix" => "https"
        //     "serverport" => "77777"
        // )
        // ```
        $this->moduleParams = $moduleParams;
    }

    public function metrics()
    {
        return [
            new Metric(
                'emailaddr',
                'Email Mailboxes',
                MetricInterface::TYPE_SNAPSHOT,
                new Accounts('Mailboxes')
            ),
        ];
    }

    public function usage()
    {
        $serverData = $this->apiCall('stats');
        $usage = [];
        foreach ($serverData as $data) {
            $usage[$data['username']] = $this->wrapUserData($data);
        }
        
        return $usage;
    }
    
    public function tenantUsage($tenant)
    {
        $userData = $this->apiCall('user_stats');
        
        return $this->wrapUserData($userData);
    }

    private function wrapUserData($data)
    {
        $wrapped = [];
        foreach ($this->metrics() as $metric) {
            $key = $metric->systemName();
            if ($data[$key]) {
                $value = $data[$key];
                $metric = $metric->withUsage(
                    new Usage($value)
                );
            }
            
            $wrapped[] = $metric;
        }
        
        return $wrapped;
    }
    
    private function apiCall($action)
    {
        // make remote call with $moduleParams
    }
}
```

The MetricProvider function will be invoked in various contexts throughout WHMCS
so it is important to utilize strategies in your class design that minimize
communication with remote servers.  The usage() and tenantUsage() methods will
only be invoked in the context of a service with a server.  However, the metrics()
method will be invoked in contexts specifically about Products. This method
must always return a valid list for all potential servers that use the module.

### Example MetricProvider Function <a id="example-function"></a>

```
use WHMCS\Module\Server\MyModule\MyMetricsProvider;

function mymodule_MetricProvider($params) {

    return new MyMetricProvider($params);
}
```

## Metrics
The metric() method must return an array of \WHMCS\UsageBilling\Contracts\Metrics\MetricInterface 
instances, as noted by the ProviderInterface.  You may use, or extend, \WHMCS\UsageBilling\Metrics\Metric

### Metric Type
The metric type of your MetricInterface instance is a critical expression of 
if/when the remote system is resetting the usage data.  If the incorrect type is
used the snapshot data stored within WHMCS may track usage incorrectly.

For metrics that are related to non-ephemeral entities, such as mailboxes, disk 
usage, or databases, your remote system is unlikely to reset this data.  These
are a "snapshot" type (\WHMCS\UsageBilling\Contracts\Metrics\MetricInterface::TYPE_SNAPSHOT)

For metrics that are related to usage that is an accumulative measure at the
remote system, like bandwidth, it is likely that these will be reset of a 
specific frequency.  WHMCS support a "time-based" daily and a monthly frequency via \WHMCS\UsageBilling\Contracts\Metrics\MetricInterface::TYPE_PERIOD_DAY
and \WHMCS\UsageBilling\Contracts\Metrics\MetricInterface::TYPE_PERIOD_MONTH. When data
is collected by WHMCS, the value of these metrics will overwrite any previous
data for the respective time period.  So for monthly items, WHMCS internals will
manage one record for each calendar month; for daily, WHMCS will manage on
record for each day of each month.  At the end of a service's billing term, any
uninvoiced usage for those periods will be summed and calculations applied to
that total.
  
### Metric Units
Several unit classes are readily available in the \WHMCS\UsageBilling\Metrics\Units
namespace.  These include Bytes, MegaBytes, GigaBytes, Accounts, and Domains.  These
extend one of the two base concrete classes, WholeNumber or FloatingPoint. You can use
those directly or extend them with your own concrete definition if you have need
for repeated use of a custom unit.

## Usage
Metrics should describe usage by providing an object that implements
\WHMCS\UsageBilling\Contracts\Metrics\UsageInterface.
You may use \WHMCS\UsageBilling\Metrics\Usage if you wish.  You will provide this
usage detail via the usage() and tenantUsage() methods.

If usage values returned by your API are not in the units that you wish WHMCS to
report has, you will need to manage any conversion.

The usage() method should return an array of tenants and a list of metrics with
usage (in the form of an object instance that implements \WHMCS\UsageBilling\Contracts\Metrics\UsageInterface).
This method is use in a global context, such as by the cron when polling for all
metric information.

The tenantUsage($tenant) should simply provide the list of MetricInterface objects
 that have been populated with UsageInterface objects.  This method
is used in specific contexts of a service. 

 
