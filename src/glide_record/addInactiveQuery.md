# addInactiveQuery()
Appends `active=false` to the encoded query of the GlideRecord. Ordering matters,
i.e. calling `addInctiveQuery()` before adding a query will append `active=false`
first while calling `addInactiveQuery()` after adding a query will append
`active=false` to the end.

## Parameters: None

## Returns: String
Return the following string: `active=false`

## Mutates Self?
Yes, the gliderecords encoded query will have `active=false` appended to it which is a mutation of self.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.addEncodedQuery('nameSTARTSWITHjohn');
userGr.addInactiveQuery();

gs.print('Example 1: '+userGr.getEncodedQuery());

userGr.initialize();
userGr.addInactiveQuery();
userGr.addEncodedQuery('nameSTARTSWITHjohn');

gs.print('Example 2: '+userGr.getEncodedQuery());
```
**Output**
```
Example 1: nameSTARTSWITHjohn^active=false
Example 2: active=false^nameSTARTSWITHjohn
```
