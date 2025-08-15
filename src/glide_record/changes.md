# changes()
This method is used to tell if a field within a GlideRecord changes in a business rule.

## Parameters: None

## Returns: Bool
A boolean representing whether the current field for a record has changed in a business rule.

## Mutates Self?
As far as I can tell, no.

## Examples:

**Script**
```js
//current is a GlideRecord('incident') in business rule's script
gs.print(current.sys_updated_on.changes());
```
**Output**
```
true
```
