# disableSysIdInOptimization
Disables certain indexing optomizations when querying by a large set of IDs.

## Parameters: None

## Returns: None

## Mutates Self?
Yes

## Examples:

**Script**
```js
var a_large_list_of_sys_ids = [
// 200 ids...
].toString();
var incidentGr = new GlideRecord('incident');
incidentGr.addEncodedQuery('sys_idIN'+a_large_list_of_sys_ids);
incidentGr.query();
gs.print(incidentGr.getRowCount());
incidentGr.addEncodedQuery('sys_idIN'+a_large_list_of_sys_ids);
incidentGr.disableSysIdInOptimization();
incidentGr.query();
gs.print(incidentGr.getRowCount());
```

**Output**
```
possibly an incorrect count
200
```
