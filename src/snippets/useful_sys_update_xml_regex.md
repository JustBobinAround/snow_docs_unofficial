# Useful sys_update_xml regex
Quickly splits target names from tables like sys_update_xml.

## Snippet
```js
var updateGr = new GlideRecord('sys_update_xml');
updateGr.query();
if (updateGr.next()) {
  var match = updateGr.getDisplayValue().match(/([a-zA-Z_]*)_([a-z0-9]{32})/);
  gs.print(match[0]);
  gs.print(match[1]);
  gs.print(match[2]);
  
}
```

### Output
```
sys_template_da3b96561b4cbd1070295538624bcb5c
sys_template
da3b96561b4cbd1070295538624bcb5c
```
