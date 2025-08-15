# canWrite()
This method checks against table level ACLs and returns a boolean representing
whether the current user can write a record for the current GlideRecord table.

For better performance and grainularity, please see [GlideSecurityManager](/glide_security_manager.md)

## Parameters: None

## Returns: Bool
A boolean representing whether the current user can write a record for the current GlideRecord table.

## Mutates Self?
As far as I can tell, no.

## Examples:

**Script**
```js
var incidentGr = new GlideRecord('incident');
gs.print(incidentGr.canWrite());
```
**Output**
```
true
```
