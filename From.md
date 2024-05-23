# Keyword `FROM`

Syntax:
```sql
    SELECT ... FROM (table1|from-function|json-object|parameter), table2...
    SEARCH selectors FROM (table|json-objects|from-function|parameter)
```

From database table
```js
    alasql('SELECT * FROM albums');
    alasql('SELECT * FROM mydb.test');
```
From parameter
```js
    alasql(‘SELECT * FROM ?’,[singers]);
```

From array parameter
```js
    alasql(‘SELECT * FROM [?]’,[singers]);
```

From file (FROM-function)
```js
    alasql('SELECT * FROM XLSX(“medals.xlsx”)');
```

From stdin (for Node.js)
```js
    alasql('SELECT * FROM TXT()');
```

From SELECT statement
```js
    alasql('SELECT * FROM (SELECT * FROM  (SELECT * FROM City))');
```

## From functions
* [[TXT]]
* [[JSON]]
* [[CSV]]
* [[TSV]]
* [[TAB]]
* [[XLSX]] 
* [[XLS]]
* [[HTML]]
* [[JSONL]] / [[JSONS]] / [[NDJSON]]

## From parameters (? and [?])

* ? – just value
* [?] – converts array to array of arrays

```js
    [1,2,3] => [[1],[2],[3]]
```

Array of objects
```js
     alasql(‘SELECT city.population FROM ? AS city’,[city]);
```
Array of arrays
```ja
     alasql(‘SELECT [0]+[1]*[2] FROM ?’, [data]);
```
Object
```js
     alasql(“SELECT [1] FROM ? WHERE [0] = ‘one’”,[{one:1,two:2}])
```
String
```js
    alasql(“SELECT LEN([0]) FROM ?”,[“Multi \n line \n text”])
```

## Parameter data type conversion
String => array of lines
```js
    alasql('SELECT * FROM ? WHERE LEN([0]) > 10',[“abc\ncde”])
    => [[“abc”],[“cde”]]
```

Objects => array of pairs key-value
```js
    {a:1,b:2} => [[“a”,1],[“b”,2]]
```

## Table Alias
FROM  table alias

```js
    alasql('SELECT * FROM ? City');
    alasql('SELECT * FROM album AS a');
```

Examples:

```js
    alasql('SELECT * FROM cities');
```

```js
    var data = [{city:"Boston"}, {city:"Los Angeles"}];
    alasql('SELECT * FROM ? ORDER BY city',[data]);
```

You can also get data from stdin stream (for Node.js only). For example, how to calculate
number of lines in incoming text file:
```js
    alasql('SELECT COUNT(*) FROM TXT()');
``` 

Please note that you can avoid letting AlaSQL try to add extension to filenames by setting `autoExt:false` in the options given. 

See also: [SELECT](Select), [SEARCH](Search)