# applyTemplate(templateName)
Applys a template to a GlideRecord. Use with caution as this function uses a templates name instead of a templates id which means there could be conflicts.

Its much safer to use the [GlideTemplate](/glide_template.md) API. See GlideTemplate's [apply](/glide_template/apply.md) method for more information.
## Parameters:
- **templateName**: String

## Returns: None

## Mutates Self?
Yes, changes the field values of a gliderecord.

## Examples:

**Script**
```js
var userGr = new GlideRecord('sys_user');
userGr.applyTemplate('some template that sets first_name to john');
gs.print(userGr.first_name.toString());
```
**Output**
```
john
```
