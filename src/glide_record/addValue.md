# addValue(fieldName, value)
Atomic adding methods Kind of a strange method. This allows the update counter
to be updated at a local level prior to actual database updates with `update()`.
## Parameters:
- **fieldName**: String
- **value**: String

## Returns: String
Returns the encoded query equivalent to what was provided in the methods parameters. Seems to be a bit unrelyable, see example...

## Mutates Self?
Yes, the GlideRecord's internal encoded query will be modified.

## Examples:

**Script**
```js

```
**Output**
```
```
