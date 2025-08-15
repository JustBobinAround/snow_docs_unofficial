# deleteMultiple()
Delete all records that meet the criteria provided by the GlideRecord's query.

This is done at the Database level, instead of from the javascript runtime, so the performance is much better.

## Parameters: None

## Returns: None

## Mutates Self?
Nope

## Examples:

**Script**
```js
var syslogGr = new GlideRecord('syslog');
syslogGr.addEncodedQuery('message=a lot of spam');
syslogGr.query();
while(syslogGr.next()) {
  //bad performance
  syslogGr.deleteRecord();
}

var syslogGr = new GlideRecord('syslog');
syslogGr.addEncodedQuery('message=a lot of spam');
syslogGr.query();
//good performance
syslogGr.deleteMultiple();
```
