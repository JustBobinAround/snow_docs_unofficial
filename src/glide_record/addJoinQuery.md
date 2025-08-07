# addJoinQuery(table, primaryField, foreignField)
Filter query results to records that have matching field values to a foreign table's field.

## Parameters:
- **table**: String
- **primaryField**: String
- **foreignField**: String

## Returns: String
Returns `<primaryField>INnull`. I guess this is probably some sort of shorthand for `JOIN`

## Mutates Self?
Yes, the gliderecord's internal encoded query will be modified.

## Examples:

**Script**
```js
var incidentGr = new GlideRecord('incident'); 
incidentGr.addJoinQuery('change_request','caller_id', 'opened_by');
incidentGr.query();
var incident_users = {};
while(incidentGr.next()) {
  incident_users[incidentGr.caller_id.getDisplayValue()] = true;
}

var changeGr = new GlideRecord('change_request'); 
changeGr.addJoinQuery('incident','opened_by','caller_id');
changeGr.query();
var change_users = {};
while(changeGr.next()) {
  change_users[changeGr.opened_by.getDisplayValue()] = true;
}

for(var user in incident_users) {
  gs.print('incident has Change User '+user+'?: '+ change_users[user]);
}
```
**Output**
```
incident has Change User Don Goodliffe?: true
incident has Change User System Administrator?: true
```
