# addActiveQuery
Appends `active=true` to the encoded query of the GlideRecord. Ordering matters,
i.e. calling `addActiveQuery()` before adding a query will append `active=true`
first while calling `addActiveQuery()` after adding a query will append
`active=true` to the end.

## Parameters: None

## Returns: String
Return the following string: `active=true`

## Mutates Self?
Yes, the gliderecords encoded query will have `active=true` appended to it which is a mutation of self.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.addEncodedQuery('nameSTARTSWITHjohn');
userGr.addActiveQuery();

gs.print('Example 1: '+userGr.getEncodedQuery());

userGr.initialize();
userGr.addActiveQuery();
userGr.addEncodedQuery('nameSTARTSWITHjohn');

gs.print('Example 2: '+userGr.getEncodedQuery());
```
**Output**
```
Example 1: nameSTARTSWITHjohn^active=true
Example 2: active=true^nameSTARTSWITHjohn
```
