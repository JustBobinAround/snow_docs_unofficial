# applyRowSecurity
Functionally, this pretty much just adds the functionallity that FilteredGlideRecord and GlideRecordSecure provide by enforcing ACLs during a query.
## Parameters: None

## Returns: None

## Mutates Self?
Yes, not fully sure what, but it has to store some sort of state for this to work.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.applyRowSecurity();
userGr.addEncodedQuery('some query that returns restricted records');
userGr.query();
gs.print(userGr.next()); // no sensitive records are returned, ACLs are enforced
```
**Output**
```
false
```
