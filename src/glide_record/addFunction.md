# addFunction
Allows for queries to be built using the [GlideDBFunctionBuilder](/glide_db_function_builder.md) object.

## Parameters:
- **functionBuilder**: GlideDBFunctionBuilder

## Returns: None

## Mutates Self?
Yes but, I'm not fully sure what gets mutated though.

## Examples:

**Script**
```js
var fb = new GlideDBFunctionBuilder();
var dbFunction = fb.position();
dbFunction = fb.constant('my'); // search_term: Text to search for in the specified table column.
dbFunction = fb.field('short_description');  // column: Name of the table column to search.
dbFunction = fb.build();

gs.print(dbFunction);

var incidentGr = new GlideRecord('incident'); // Table containing the column to search
incidentGr.addFunction(dbFunction);
incidentGr.addQuery("short_description", "CONTAINS", "my");
incidentGr.setLimit(20);
incidentGr.query();
while(incidentGr.next()) {
  gs.print(incidentGr.short_description + "\n position('my', short_description): " + incidentGr.getValue(dbFunction));
}
```
**Output**
```
glidefunction:position('my',short_description)
My computer is not detecting the headphone device
position('my', short_description): 1
Reset my password
position('my', short_description): 7
Missing my home directory
position('my', short_description): 9
Seem to have an issue with my hard drive...
position('my', short_description): 28
My disk is still having issues. Can't delete a file
position('my', short_description): 1
Reset my password
position('my', short_description): 7
my PDF docs are all locked from editing
position('my', short_description): 1
Printer in my office is out of toner
position('my', short_description): 12
The USB port on my PC stopped working
position('my', short_description): 17
I can't launch my VPN client since the last software update
position('my', short_description): 16
Please remove the latest hotfix from my PC
position('my', short_description): 38
I can't get my weather report
position('my', short_description): 13
My desk phone does not work
position('my', short_description): 1
Can't log into SAP from my laptop today
position('my', short_description): 25
Wireless access is down in my area
position('my', short_description): 28
```
