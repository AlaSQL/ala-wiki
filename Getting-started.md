# Getting Started


After [including/requiring/installing AlaSQL](install) the object `alasql` is the main variable of the module. You can use it immediately as a default database

In browser:
```html
    <script src="alasql.js"></script>
    <script>
        alasql('CREATE TABLE one (two INT)');
    </script>
```
_Try this sample in [AlaSQL console](http://alasql.org/console?CREATE TABLE one (two-INT))_


or in Node.js:
```js
    var alasql = require('alasql');
    alasql('CREATE TABLE one (two INT)');
```

Another approach is to create new database:

```js
    var mybase = new alasql.Database();
    mybase.exec('CREATE TABLE one (two INT)');
```
You can give a name to database and then access it from alasql:
```js
    var mybase = new alasql.Database('mybase');
    console.log(alasql.databases.mybase);
```

Each database can be used with the following methods:

```js
    var db = new alasql.Database() - create new alasql-database
    var res = db.exec("SELECT * FROM one") - executes SELECT query and returns array of objects 
```

Usually, alasql.js works synchronously, but you can use callback.

```js
    db.exec('SELECT * FROM test', [], function(res){
        console.log(res);
    });
```

or you can use promise() 

```js
    alasql.promise('SELECT * FROM test')
    .then(function(res){
        // Process data
    }).catch(function(err){
        // Process errors
    });
```
You can use compile statements:
```js
    var insert = db.compile('INSERT INTO one (1,2)');
    insert();
```

You can use parameters in compiled and interpreted statements:

```js
    var insert1 = db.compile('INSERT INTO one (?,?)');
    var insert2 = db.compile('INSERT INTO one ($a,$b)');
    var insert3 = db.compile('INSERT INTO one (:a,:b)');

    insert1([1,2]);
    insert2({a:1,b:2});
    insert3({a:3,b:4});

    db.exec('INSERT INTO one (?,?)',[5,6]);

```
You even can use param in FROM clause: 

```js
        var years = [
            {yearid: 2012}, {yearid: 2013},
            {yearid: 2014}, {yearid: 2015},
            {yearid: 2016},
        ];

        var res = alasql.queryArray('SELECT * FROM ? AS years ' +
            'WHERE yearid > ?', [years,2014]);

        // res == [2015,2016]
```

----
#### Work directly on JSON data

Work directly on JSON data and group JavaScript array by field and count number of records in each group:

```js
    var data = [{a:1,b:1,c:1},{a:1,b:2,c:1},{a:1,b:3,c:1}, {a:2,b:1,c:1}];
   
    var res = alasql('SELECT a, COUNT(*) AS b FROM ? GROUP BY a',[data]);
    console.log(res);
```

----

#### Array of arrays
You can use array of arrays to make a query. In this case use square brackets for column name,
like \[1\] or table\[2\] (remember, all arrays in JavaScript start with 0):

```js
        var data = [
            [2014, 1, 1], [2015, 2, 1],
            [2016, 3, 1], [2017, 4, 2],
            [2018, 5, 3], [2019, 6, 3]
        ];
        var res = alasql('SELECT SUM([1]) FROM ? d WHERE [0]>2016', [data]);
```
Use alasql.queryArrayOfArrays() function to return array of arrays. In this case
you can specify array position of selected column with number or number in brackets:
```js
        var res = alasql.queryArrayOfArrays(
            'SELECT [1] AS 0,[1]+[2] AS [1] FROM ? d WHERE [0]>2016', [data]);
```
This feature can be used as filter for arrays:
```js
        // Same filter
        var res1 = alasql.queryArrayOfArrays('SELECT * FROM ? a WHERE [0]>2016', [data]);
        var res2 = data.filter(function(a){return a[0]>2016});

        // Complex filter with aggregating, grouping and sorting
        var res = alasql.queryArrayOfArrays(
            'SELECT [2] AS 0, SUM([1]) AS 1 FROM ? a WHERE a[0]>? GROUP BY [0] ORDER BY [1]', 
            [data, 2016]);

```

----

#### Work with IndexedDB database with SQL: 

Attach IndexedDB database, and then complex query on two joined tables and filtering:
 
```js
    alasql(’ATTACH INDEXEDDB DATABASE MyBase; \ 
            USE MyBase; \
            SELECT City.* \
                   FROM City \
                   JOIN Country USING CountryCode \
                   WHERE Country.Continent = ”Asia”’, [], function (res) {
              console.log(res.pop());
    }); 
```

----


#### In browser multi-line SQL statements:

```html
    <script src="http://alasql.org/console/alasql.min.js"></script>
    <div id="res"></div>
    <script type="text/sql" id="sql">
    CREATE TABLE people (
        Id INT PRIMARY KEY,
        FirstName STRING,
        LastName STRING
    );
    
    INSERT INTO people VALUES 
        (1,"Peter","Peterson"),
        (2,"Eric","Ericson"),
        (3,"John","Johnson");

    IF EXISTS (SELECT * FROM people WHERE Id=2)
        UPDATE people SET FirstName = "Roll", LastName = "Rolson" WHERE Id=2
    ELSE
        INSERT INTO people VALUES (2,"Eric","Rollson");

    IF EXISTS (SELECT * FROM people WHERE Id=4)
        UPDATE people SET FirstName = "Roll", LastName = "Rolson" WHERE Id=4
    ELSE
        INSERT INTO people VALUES (4,"Smith","Smithson");

    SELECT * INTO HTML("#res",{headers:true}) FROM people;
    </script>
    <script>
        alasql('SOURCE "#res"');
    </script>
```
Try this example [in jsFiddle](http://jsfiddle.net/agershun/n4de6433/4/)

----



See also [this slide](http://www.slideshare.net/AndreyGershun/alasql-manual-141220-1) for more inspiration

