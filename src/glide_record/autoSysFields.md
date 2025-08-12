# autoSysFields(updateFields)
Extends functionality of [setWorkflow](/glide_record/setWorkflow.md) method to
include not updating system fields like `sys_updated_on`, `sys_updated_by`, etc.

This method is useful for creating test data for scripts that are dependent on
system fields. This method along with `setWorkflow(false)` achieves basically
the same behavior as an xml import of a record.

After using `autoSysFields(false)` on a GlideRecord in a business rule, make
sure to call `autoSysFields(true)` before the business script ends. I have
seen cases where this roles over to following business rules and can have bad
consequences.

## Parameters:
- **updateFields**: bool

## Returns: None

## Mutates Self?
Yes, this is just a setter for an internal flag.

## Examples:

**Script**
```js
var incidentGr = new GlideRecord('incident');
incidentGr.orderByDesc('sys_created_on');
incidentGr.query();
if (incidentGr.next()) {
  incidentGr.setWorkflow(false);
  incidentGr.autoSysFields(false);
  var current_date_time = (new GlideDateTime()).toString();
  gs.print(incidentGr.sys_updated_on.toString());
  gs.print(current_date_time);
  incidentGr.setValue('sys_created_on', current_date_time);
  incidentGr.setValue('sys_updated_on', current_date_time);
  incidentGr.update();
  incidentGr.setWorkflow(true);
  incidentGr.autoSysFields(true);
  gs.print(incidentGr.sys_updated_on.toString());
}
```
**Output**
```
2025-07-22 15:17:25
2025-08-12 13:50:28
2025-08-12 13:50:28
```
