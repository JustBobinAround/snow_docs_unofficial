# addQuery(fieldName, op, value)
Helper method to append to encoded query in a more
functional way. Instead of building a String and adding with
[addEncodedQuery](/glide_record/add_encoded_query.md), a user
can append to the query by providing parameters like `addQuery('name', 'STARTSWITH', 'john')`.

## Parameters:
- **fieldName**: String
- **op**: Option<String>
- **value**: String

## Returns: String
Returns the encoded query equivalent to what was provided in the methods parameters. Seems to be a bit unrelyable, see example...

## Mutates Self?
Yes, the GlideRecord's internal encoded query will be modified.

## Operators

### Number Operators
- **=**: Equals
- **!=**: Does not equal
- **>**: Greater than
- **>=**: Greater than or equal to
- **<**: Less than
- **<=**: Less than or equal to

### String Operators
- **=**: Equals
- **!=**: Does not equal
- **STARTSWITH**: Any String that starts with <value>
- **ENDSWITH**: Any String that ends with <value>
- **CONTAINS**: Any String that contains <value>
- **LIKE**: Any String that contains <value>
- **DOES NOT CONTAIN**: Any String that does not contain <value>
- **NOT LIKE**: Any String that does not contain <value>
- **IN**: Any string that is equal to one of the comma delimited Strings within <value>
- **NOT IN**: Any string that is not equal to one of the comma delimited Strings within <value>
- **INSTANCEOF**: Any record that is a child class of the class provided in <value>

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
gs.print(userGr.addQuery('name', 'CONTAINS', 'john'));
gs.print(userGr.getEncodedQuery());
```
**Output**
```
nameLIKEjohn
nameCONTAINSjohn
```
