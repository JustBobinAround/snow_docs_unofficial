# addNullQuery
Filters for records where a specific field is null. This is technically
different than ISNOTEMPTY in a query. Basically, null is empty, but empty is not
always null. A null field is usually produced by older records where a field may
not have existed at the time.

Functionally, this just appends `<fieldName>=NULL` to the GlideRecord's internal encoded query.

## Parameters:
- **fieldName**: String

## Returns: String
Returns `<fieldName>=NULL`.

## Mutates Self?
Yes, the gliderecord's internal encoded query will be modified.

## Examples:

**Script**
```js
//TODO: this is throwing error rn and I don't know why
var incidentGr = new GlideRecord('incident'); 
gs.print(incidentGr.addNullQuery('caller_id'));
gs.print(incidentGr.getEncodedQuery());
```
**Output**
```
```
