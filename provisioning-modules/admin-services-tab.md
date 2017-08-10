+++
prev = "/provisioning-modules/client-area-output"
next = "/provisioning-modules/admin-dashboard-widgets"
title = "Admin Services Tab"
toc = true
weight = 90

+++

Admin Services Tab functions allow definition of extra fields to appear on the product details in the admin area.
Used for informational output, or for settings and values stored in custom tables or outside WHMCS.

WHMCS uses this in the core system for our licensing addon module.
The license specific fields of the allowed system are set and viewed from the product details.

There are 2 functions relating to the services tab - `AdminServicesTabFields` and `AdminServicesTabFieldsSave`.
The first of these allows definition of the extra fields to output.
The latter allows handling any input on submission/save, if required.

So on to an example, below we show you how to define 4 extra fields.
This example shows an input, dropdown, textarea and info only output.
The examples continues to update them in a custom table of the database via the save event.

## Example Admin Services Tab Function <a id="example-function"></a>

```
function mymodule_AdminServicesTabFields($params) {

    $result = select_query(
        "mod_customtable",
        "",
        array("serviceid" => $params['serviceid'],)
    );
    $data = mysql_fetch_array($result);
    $var1 = $data['var1'];
    $var2 = $data['var2'];
    $var3 = $data['var3'];
    $var4 = $data['var4'];

    $fieldsarray = array(
     'Field 1' => '<input type="text" name="modulefields[0]" size="30" value="'.$var1.'" />',
     'Field 2' => '<select name="modulefields[1]"><option>Val1</option</select>',
     'Field 3' => '<textarea name="modulefields[2]" rows="2" cols="80">'.$var3.'</textarea>',
     'Field 4' => $var4, # Info Output Only
    );
    return $fieldsarray;

}

function mymodule_AdminServicesTabFieldsSave($params) {
    update_query("mod_customtable",array(
        "var1"=>$_POST['modulefields'][0],
        "var2"=>$_POST['modulefields'][1],
        "var3"=>$_POST['modulefields'][2],
    ),array("serviceid"=>$params['serviceid']));
}
```
