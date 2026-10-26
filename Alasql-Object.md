# The AlaSQL Object

## Properties and functions - overview

In the following the term `sql` is ment as a string contaning SQL statements.


* `alasql(sql)` - short for `alasql.exec(sql)`

* `alasql.exec(sql)`- executes SQL and returns responses. If several SQL statements are given (seperated by `;`) the return value will be an array with the response of each statement. Statments that does not `SELECT` data will return an int indicating rows affected or if the execution of the statement succeeded.

* `alasql(sql,params)` – short for `alasql.exec(sql,params)`

* `alasql.exec(sql,params)` executes SQL after having replaces the n'th `?` in sql with the n'th index in the array `params`

* `alasql(sql,params,callback)` – short for `alasql.exec(sql,params,callback)`

* `alasql.exec(sql,params,callback)` - adding a 3rd parameter will run the SQL async calling the callback with one parameter (the response) when finished.

* `alasql(data)` - starting poit for [fluent interface](Fluent-Interface)


* `alasql.parse(sql)` – parse SQL to an [abstract syntax tree (ATS)](AST)


* `alasql.compile(sql)` – returns compiled statement (and adds it to database cache)


* `alasql.use(databaseid)` – Equivalent to `alasql('USE '+databaseid)`. See also [the keyword USE](Use-Database)

* `alasql.pretty(sql)` – "prettyfys" SQL statements

* `alasql.options.*` - See [options](AlaSQL-Options) for more inforamtion

* `alasql.databases` - array of databases in the AlaSQL object

* `alasql.tables` - Array of the tables in the default database (called `alasql`)


## In more details

### alasql() - main function
```js
    alasql(sql,[params],[callback])
```

**sql** – one or some SQL-statements separated by ‘;’
If one statement – alasql() returns one value
```sql
    USE test12 => 1
    SELECT * FROM one => [{a:1}, {a:2}]
```

If some statements – alasql() returns array of values, one for each statement
```sql
    USE test12; SELECT * FROM one => [1,[{a:1}, {a:2}]]
```

**params** – an array of parameters of SQL statement
You can use ? in SQL statement
```js
    alasql(‘SELECT a FROM ? WHERE b = ?’,[[{a:1,b:1}, {a:2,b:2}],2])
```
**callback** – a callback function
* Without callback alasql() runs synchroniously
* With callback alasql() runs asynchroniously with callbacks

See [Sync and Async](Async).

## How to use alasql()

*alasql* is a main object and function of AlaSQL library. It can be used in some different ways:  

```html
    <script src="alasql.js"></script>
    <script>
    	alasql('create table capitals (country string, city string, population int)');
    	alasql('insert into capitals values ("USA", "Washington, D.C.", 646449)');
    	alasql('insert into capitals values ("France", "Paris", 2211000)');
    	alasql('insert into capitals values ("Russia", "Moscow", 11500000)');
    	alasql('insert into capitals values ("Mexica", "Mexico City", 8851000)');
    	alasql.log('select city,population from capitals order by population desc');
    </string>
```

1. Execute SQL statement or set of statements:
```js
    alasql(sql-statement)
```

2. Class for a number functions:
* alasql.exec(sql, params, callback) - execute SQL statement
* alasql.value(sql, params, callback) - execute SQL statement but return only one value
* alasql.log(sql, params) - execute SQL statement and log the results to console or into HTML tag

3. Class for options:
* alasql.options.logtarget - target for alasql.log() functions. Values can be "console" or HTML tag

### List of databases

You can find list of current tables in alasql.databases property:
```js
	console.log(Object.keys(alasql.databases).sort().join(', '));
```
### List of tables

You can find list of current tables in alasql.tables property:
```js
	console.log(Object.keys(alasql.tables).sort().join(', '));
```