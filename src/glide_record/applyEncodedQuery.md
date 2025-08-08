# applyEncodedQuery(query)
Allows fields to be set via encoded query. Useful for populating a form via url, just make sure to properly sanatize things.
## Parameters:
- **query**: String

## Returns: None

## Mutates Self?
Yes, the GlideRecord's internal field states are changed based on the encoded query.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.initialize();
userGr.applyEncodedQuery('first_name=john^last_name=smith');
gs.print(userGr.first_name.toString());
gs.print(userGr.last_name.toString());
```
**Output**
```
john
smith
```
