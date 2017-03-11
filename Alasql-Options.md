# AlaSQL Options

You can find all AlaSQL options in the `alasql.options` variable. The options are global for all databases - also if you create them with `new`.

You can change these options directly from JavaScript:

```js
    alasql.options.autocommit = true;
```
or from SQL with the [`SET`](Set) statement:

```sql
    SET AUTOCOMMIT OFF;
    SET MODIFIER = "RECORDSET";
```

Setting them via the `SET` statement is the only option when running from the console or if you run as a webworker and want to change options during executions. 

### List of AlaSQL options

* alasql.options.valueof (true/false) – convert all values with .valueOf() function before comparing
* alasql.options.angularjs (true/false) – remove $$hashKey from result arrays if angular.js library loaded 
* alasql.options.errorlog = false; // Log or throw error
* alasql.options.valueof = false; // Use valueof in orderfn
* alasql.options.dropifnotexists = false; // DROP database in any case
* alasql.options.datetimeformat = 'sql'; // How to handle DATE and DATETIME types
* alasql.options.casesensitive = true; // Table and column names are case sensitive and converted to lower-case
* alasql.options.logtarget = 'output'; // target for log. Values: 'console', 'output', 'id' of html tag
* alasql.options.logprompt = true; // Print SQL at log
* alasql.options.modifier = undefined; // values: RECORDSET, VALUE, ROW, COLUMN, MATRIX, TEXTSTRING, INDEX
* alasql.options.columnlookup = 10;  // How many rows to lookup to define columns
* alasql.options.autovertex = true;// Create vertex if not found
* alasql.options.usedbo = true; // Use dbo as current database (for partial T-SQL comaptibility)
* alasql.options.autocommit = true; // AUTOCOMMIT ON | OFF
* alasql.options.cache = true; // Use cache
* alasql.options.nocount = false;// for SET NOCOUNT OFF
* alasql.options.nan = false;// Check for NaN and convert it to undefined

#### Compatibility flags (not in use at the moment)
* alasql.options.tsql = true;
* alasql.options.mysql = true;
* alasql.options.postgres = true;
* alasql.options.oracle = true;
* alasql.options.sqlite = true;
* alasql.options.orientdb = true;

