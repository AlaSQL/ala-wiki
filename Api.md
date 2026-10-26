# AlaSQL JavaScript API

## Normal ussage:

* alasql(stringWithSQL)
* alasql.compile(stringWithSQL) - [Pre compile statements](Compile)

Please see more info about the [`alasql` object here](alasql-object)


## SQL driven data insert
```js
    alasql(‘CREATE DATABASE test01’);
    alasql(‘USE test01’);
    alasql(‘CREATE TABLE one (a INT)’);
    alasql(‘INSERT INTO one VALUES (10)’):
    var res = alasql(‘SELECT * FROM one’);
```

## JavaScript driven data insert
```js
    var data = [{a:1}, {a:2}, {a:3}];
    alasql(‘SELECT * FROM ? WHERE a >= ?’, [data, 2]);

    // or
    var db = new alasql.Database();
    db.exec(“select * from one”, function(data) {
        console.log(data.length);
    });
```
## Promises
AlaSQL supports promises with `alasql.promise(sql,params)` function. It returns a standard A/+ promise:

```js
    alasql.promise('SELECT * FROM test')
    }).then(function(res){
        // Process data
    }).catch(function(err){
        // Process errors
    });
```


## new database

```js
    var db = new alasql.Database(‘mydb’);
    db.exec(‘SELECT * FROM City”);
```

## JavaScript classes as SQL data types
```js
    alasql.fn.Date = Date;
    alasql('CREATE order (orderno INT, orderdate Date)');
```

***NB.*** Classes are case-sensitive

## NEW (like JavaScript ‘new’ operator)

Register class as alasql type
```js
    alasql.fn.Date = Date;
```
Use NEW
```js
    alasql(‘SELECT NEW Date(yr,mn-1,dy) FROM orderdates’)
```

## JSON Objects usage
Please See [JSON Objects](Json-Objects)

