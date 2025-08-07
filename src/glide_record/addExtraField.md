# addExtraField
Allows for better dot walking performance by front loading certain pieces of a child record with the intial encodedQuery.


## Parameters:
- **dotWalk**: String

## Returns: None

## Mutates Self?
Yes, the gliderecord's internal encoded query will be modified.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.addEncodedQuery('companyISNOTEMPTY');
userGr.query();
if(userGr.next()) {
	//requires two queries
  gs.print(userGr.company.city.toString());
}


userGr.initialize();
userGr.addEncodedQuery('companyISNOTEMPTY');
userGr.addExtraField('company.city');
userGr.query();
if(userGr.next()) {
  //requires one query
  gs.print(userGr.company.city.toString());
}
```
