# deleteRecord()
Deletes the current GlideRecord.

## Parameters: None

## Returns: None

## Mutates Self?
Yes

## Examples:

**Script**
```js
var incidentGr = new GlideRecord('incident');
incidentGr.query();
if(incidentGr.next()) {
  var sys_id = incidentGr.sys_id.toString();
  incidentGr.deleteRecord();
  if(incidentGr.get(sys_id)) {
    gs.print('record found');
  } else {
    gs.print('record not found');
  }
}

```

**Output**
```
record not found
```
