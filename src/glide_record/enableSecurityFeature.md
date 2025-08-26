# enableSecurityFeature()
Enables usage of security data features as filters for a GlideRecord instance. Security data features
are query definitions that are found in the `sys_security_data_filter` table. The queries will be added
depending on the table. Since this mutates the GlideRecord's query and not overarching ACLs, the `canRead`
method may still return true for a record instance if already aquired by the GlideRecord prior to reinitialization.


## Parameters: None

## Returns: None

## Mutates Self?
Yes, this is just a setter for an internal flag.

## Examples:

**Script**
```js
//assumption: incident table has a Security Data Feature record
var incidentGr = new GlideRecord('incident');
incidentGr.enableSecurityFeature();
incidentGr.query();
gs.print('With security feature: '+incidentGr.getRowCount());

incidentGr.disableSecurityFeature();
incidentGr.query();
gs.print('Without security feature (larger record count returned): '+incidentGr.getRowCount());
```
**Output**
```
With security feature: 1000
Without security feature (larger record count returned): 1200
```
