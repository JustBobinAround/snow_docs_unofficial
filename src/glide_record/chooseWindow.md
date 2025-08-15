# chooseWindow(firstRow, lastRow, forceCount)
This method is useful to add a starting offset to GlideRecord's query. This can
usually be done just by adding to an encoded query, but this is usually a bit
more readable.

## Parameters:
- **firstRow**: integer
- **lastRow**: integer
- **forceCount**: integer

## Returns: None

## Mutates Self?
Yes

## Examples:

**Script**
```js
var incidentGr = new GlideRecord('incident');
incidentGr.chooseWindow(5,10,5);
incidentGr.orderBy('number');
incidentGr.query();
gs.print(incidentGr.getRowCount());
while(incidentGr.next()){
  gs.print(incidentGr.number.toString());
}
```

**Output**
```
67
INC0000006
INC0000007
INC0000008
INC0000009
INC0000010
```
