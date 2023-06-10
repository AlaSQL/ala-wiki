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


```JS
/** Log or throw error */
errorlog: false,

/** Use valueof in orderfn */
valueof: true,

/** Callback for async queries progress */
progress: false, 

/** Date separator for Now() function */
nowdateseparator: '-', 

// Date-time Separator for Now() function
nowdatetimeseparator: ' ', 

/** DROP database in any case */
dropifnotexists: false,

/** How to handle DATE and DATETIME types */
datetimeformat: 'sql',

/** Table and column names are case sensitive and converted to lower-case */
casesensitive: true,

/** target for log. Values: 'console', 'output', 'id' of html tag */
logtarget: 'output',

/** Print SQL at log */
logprompt: true,

/** Callback for async queries progress */
progress: false,

/**
 * Default modifier
 * values: RECORDSET, VALUE, ROW, COLUMN, MATRIX, TEXTSTRING, INDEX
 * @type {'RECORDSET'|'VALUE'|'ROW'|'COLUMN'|'MATRIX'|'TEXTSTRING'|'INDEX'|undefined}
 */
modifier: undefined,

/** How many rows to lookup to define columns */
columnlookup: 10,

/** Create vertex if not found */
autovertex: true,

/** Use dbo as current database (for partial T-SQL comaptibility) */
usedbo: true,

/** AUTOCOMMIT ON | OFF */
autocommit: true,

/** Use cache */
cache: true,

/** Check for NaN and convert it to undefined */
nan: false,

/** excel config*/
excel: {cellDates: true},

/** Option for SELECT * FROM a,b */
joinstar: 'overwrite',

```


