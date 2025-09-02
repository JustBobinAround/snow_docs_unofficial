# Get select box options (g_form)
Useful for checking the client side state for a set of options in a select box.

## Snippet
```js
function variable_choices(var_name) {
  // g_form.getElement() has been deprecated
  return g_form.getField(var_name).choices;
}
```
