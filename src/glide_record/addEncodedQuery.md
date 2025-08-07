# addEncodedQuery(query)
If the GlideRecords internal encoded query is not null, this will append a `^`
to the GlideRecord's internal encoded query and then append the query provided
in the method's parameters to the GlideRecord's internal encoded query.

If the GlideRecords internal encoded query is null, this will append just the
query provided in the method's parameters to the gliderecord's internal encoded
query.

## Parameters:
- **query**: String

## Returns: None

## Mutates Self?
Yes, the gliderecord's internal encoded query will be modified.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.addEncodedQuery('nameSTARTSWITHjohn');

gs.print('Example 1: '+userGr.getEncodedQuery());

userGr.addEncodedQuery('nameENDSWITHsmith');

gs.print('Example 2: '+userGr.getEncodedQuery());
```
**Output**
```
Example 1: nameSTARTSWITHjohn
Example 2: nameSTARTSWITHjohn^nameENDSWITHsmith
```
