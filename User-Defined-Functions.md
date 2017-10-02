# User defined functions

To define new functions for SQL simply add it to ```alasql.fn``` variable, like below:


```js
alasql.fn.cube = function(x) { return x*x*x; }
alasql(‘SELECT cube(x) FROM ?’,[data]);
```

```js
alasql.fn.double = function(x){return x*2};        
alasql.fn.sum10 = function(x,y) { return x+y*10; }
alasql('SELECT a, double(a) AS b, sum10(a,b) FROM test1');
```




You can use alasql inside alasql functions, like below:
```js
alasql.fn.myfilter = function(phase) {
	return alasql('SELECT VALUE COUNT(*) FROM ? WHERE Phase = ?',[data,phase]) == 2;
};

var res = alasql('SELECT * FROM ? WHERE myfilter(Phase)',[data]);
```
See the working example [in jsFiddle](http://jsfiddle.net/agershun/1nccgs6n/3/)

From 3.8 functions can be set via a SQL statement with the following syntax:

```sql
CREATE FUNCTION cubic AS ``function(x) { return x*x*x; }``;
```



## Aggregators

To make your own user defined aggregators please follow this example:

```js
// How to implement the SUM() aggregator
alasql.aggr.MYAGGR = function(value, accumulator, stage) {
	if(stage == 1) {

		// first call of aggregator - for first line
		var newAccumulator =  value;
		return newAccumulator;
	
	} else if(stage == 2) {

		// for every line in the group
		accumulator = accumulator + value;
		return accumulator;
	
	} else if(stage == 3) {

		// Post production - please nota that value Will be undefined
		return accumulator;  
	}
}
```

See more examples here:
* [50functions.js](https://github.com/agershun/alasql/blob/develop/src/55functions.js#L230-L339)
* [test266.js](https://github.com/agershun/alasql/blob/develop/test/test266.js)

## Create aggretating functions  
From 3.8 aggretating functions can be set via a async SQL statement with the following syntaxes:

```sql
CREATE (AGGREATE|AGGREGATOR) MyAggr AS ``function(value, accumulator, stage) { ... }``;
```

## Custom `FROM` function

You can create custom FROM function like here:
```
alasql.from.DB = function(dbtype, opts, cb, idx, query) {
	var res = [];
        async_read_data_from_mysql_function(dbtype, opts.dbname, opts.tablename, function(data) {
		res = data;
		if(cb){
			res = cb(res, idx, query);
		}
	};
	return null;
};

function async_read_data_from_mysql_function(dbtype, dbname, tablename, cb) {
    // put your code here
   cb(read_data);
}
```
Then you can use it like:
```sql
SELECT * FROM DB("mysql",{dbname:"one", tablename:"two"})
```

Also, you can save data to MYSQL with ```alasql.into.DB()``` custom function.
```
alasql('SELECT * INTO DB("mysql",{dbname:"one", tablename:"two"}) FROM ?',[data]);
```

You can see the examples of FROM and INTO functions at ```src/84from.js``` and ```src/830into.js``` files.






