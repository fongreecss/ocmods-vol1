# ocmods-vol1
Some OCmods for Opencart (2.2 could work on earlier versions) that I use

##alfra_disable_zone.ocmod.xml
Removes region/zone/state from register new user, guest checkout, address edit, shipping estimate, payment address forms.

##alfra_sort_by.ocmod.xml
This is a very simple file modification. It overrides `$sort` (and `$order`) default values. `$order` is by default set to `'ASC'` and `$sort` is set to `'p.sort_order'`. Make changes to this file to match your needs.

Possible `$sort` values:  
+ 'p.sort_order' - by default
+ 'pd.name'      - by name
+ 'p.price'      - by price
+ 'p.model'      - by model

Possible `$order` values:  
+ 'ASC'   - ascending
+ 'DESC'  - descending

```xml
<?xml version="1.0" encoding="utf-8"?>
<modification>
  <name>Alfra Sort By</name>
  <code>alfra_sort_by</code>
  <version>1.0</version>
  <author>alfra (fongreecss@gmail.com)</author>
  <link>http://github.com/frasaleksander</link>
    <file path="catalog/controller/product/category.php">
        <operation error="log">
            <search><![CDATA[$sort = 'p.sort_order';]]></search>
            <add position="replace"><![CDATA[
                    //options :
                    //'p.sort_order' - by default
                    //'pd.name'      - by name
                    //'p.price'      - by price
                    //'p.model'      - by model
                    $sort = 'p.price';
                ]]></add>
        </operation>
        <operation error="log">
            <search><![CDATA[$order = 'ASC';]></search>
            <add position="replace"><![CDATA[
                    //options :
                    //'ASC'   - ascending
                    //'DESC'  - descending
                    $order = 'ASC';
                ]]></add>
        </operation>
    </file>
</modification>
```
