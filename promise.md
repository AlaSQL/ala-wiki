# `Promise` notation

We strongly recommend using the promise notation for all [[async]] interactions with AlaSQL. This includes every time a filename or URL is part of the SQL.

```js
alasql.promise(sql(s) [, params])
      .then(function(data){
           // Display data
      }).catch(function(error){
           // Log the error
      });
```

The `.promise` part can be omitted if the SQL is given as an array (format documented in "Chain of promises"). Example of the lazy promise notation: 

```js
alasql(['SELECT * FROM XLS("mydata.xls") GROUP BY name WHERE lastname LIKE "A%" and city = "London"'])
      .then(function(data){
           // Display data
      }).catch(function(error){
           // Display error
      });
```

AlaSQL uses ES6 promises which are available in most modern browsers. AlaSQL brings a [polyfill](https://github.com/jakearchibald/es6-promise/blob/master/dist/es6-promise.min.js) if `Promise` is not supported. 






## Chain of promises

If you put more than one SQL command in the same string they will (until it is fixed) run sync within the async call to `alasql` - so a command like `"INSERT ...; SELECT * ..."` the second command might start before the first command is done. This is not a problem unless you are using a DB that demands async interaction (like indexedDB).

Pass an array of queries to `alasql.promise` to execute in a chain (so one after the return of the promise of the other). 

```js
alasql.promise([
	'CREATE FILESTORAGE DATABASE test123("./testDBfile.json")', 
	'ATTACH FILESTORAGE DATABASE test123("./testDBfile.json")', 
	'USE test123', 
	'CREATE TABLE IF NOT EXISTS products (id INT, category_id INT, name string, created_at DATE)', 
	['INSERT INTO products (id, category_id, name, created_at) VALUES (?,?,?,?)', [1, 2, 'XYZ', new Date()] ],
	'SELECT * FROM products'	
]).then(function(res){
	console.log('Results from all queries:',res)
}).catch(function(reason){
	console.log('Error:',reason)
})
```

Please note that to be able to combine a query with parameters instead of a string one must pass an array with the query string at index 0 and the array of parameters at index 1.


## More about promise

If you are not used to work with promises have a look at http://www.2ality.com/2014/10/es6-promises-api.html where the concepts are explained very well. Central to the usage is the concept of 

![image](http://3.bp.blogspot.com/-K9wwF9rRnJA/VDEiVbdCqDI/AAAAAAAAA4g/QkdNWpxIzEc/s1600/resolve_with_thenable.jpg)

This means you can chain .then(...) methods when they return another promise. For AlaSQL this means you can return a `alasql.promise` object from a `.then` and keep the code unnested. 

Example of the notation:
```js
alasql.promise([
                'UPDATE abc values (5)',
                'VALUE OF SELECT max(val)'
        ]).then(function(res){
                console.log('max value found:', res);
                var n = prompt('Please write a number between 0 and '+res);
                return alasql.promise('SELECT * FROM abc WHERE val = '+n)
        }).then(function(res){
                console.log('You got: ', res);
        })
```

