# Set Application to Private Scope
Go to `sys_store_app.list` and open any private application record that can normally not be set as the current users application.

Press ctrl+shift+J to open the client script runner and then run the script in the snippet section.

Hard refresh the page after just to be on the safe side. Then the private scoped
application files can be edited. This doesn't override read-only protected
files. Please feel free to submit a pull request to these docs if you know a way
around read-only protections.

## Snippet
```js
function changeCurrentApplication() {
	if (typeof rowSysId == 'undefined')
		sysId = gel('sys_uniqueValue').value;
	else
		sysId = rowSysId;
	
	jQuery.ajax('/api/now/ui/concoursepicker/application',
	{
		method: "GET",
		headers: {
			'X-UserToken': g_ck,
		}
	})
	.done(function checkIfScopeAccessIsAllowed(response) {
		if (!(response && response.result && response.result.list && Array.isArray(response.result.list))) {
			return;
		}
		
		var canUserSwitchToScope = true;
		if(!canUserSwitchToScope) {
			g_GlideUI.addOutputMessage({
				'msg': new GwtMessage().getMessage('Not allowed to switch to this application scope.'),
				'type': 'error'
			});
			return;
		}
		
		var ajax = new GlideAjax("com.snc.apps.AppsAjaxProcessor");
		ajax.addParam("sysparm_function", "changeApplication");
		ajax.addParam("sysparm_value", sysId);
		ajax.getXML(changeApplicationResponse);
	})
	.fail(function informOfScopeAccessCheckError(jqXHR, textStatus, error) {
		g_GlideUI.addOutputMessage({
			'msg': new GwtMessage().getMessage('Failed to determine if application scope is accessible. HTTP Status {0}: {1}', jqXHR.status, error),
			'type': 'error'
		});
	})
	;

	function changeApplicationResponse() {
		// in List v3, we are in UI16, so the picker refreshes automatically
		if (g_api == 2)
			return;
		
		var picker = getTopWindow().g_application_picker;
		if (picker) {
			picker.select.options.length = 0;
			picker.fillApplications();
		}
		window.location.reload();
	}
}
changeCurrentApplication();
```