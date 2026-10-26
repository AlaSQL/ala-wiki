# JSON

AlaSQL can read and store data in JSON format.

## Object Property
Property operator -> 
```sql
    INSERT INTO one VALUES @{a:5, b:{c:@[4,5]}}
    SELECT * FROM one WHERE a->b->0 = 4
```

Please note that negavie numbers must be enclosed like this: `(-5)`. There is [an issue to get it fixed](https://github.com/agershun/alasql/issues/475). 

Expression
```sql
    SELECT * FROM one WHERE a->(LCASE(“B”))->(1-1) = 4
```

## Call JavaScript object function
Arrow function ->
```js
    object -> function(parameters)
```
Select lengths of all lines from text file
```js
    alasql(‘SELECT [0]->length FROM TXT(“mytext.txt”)’
    alasql(‘SELECT LEN([0]) FROM TXT(“mytext.txt”)’
```

## JavaScript object properties
Arrow function -> property
```js
    var data = [{a:{b:1,c:1}, {a:{b:2}}}]
    alasql(‘SELECT a->b FROM ?’,[data]);
```

Array members
```sql
    SELECT a->(0) FROM data
```

Calculated property names
```sql
    SELECT a->(“mon”+moid), b->(2+2) FROM data
```

## Object Properties & Functions

Object property
* `a -> b`
* `a -> b -> c`

Array member
* `a -> 1`
* `a -> 1 -> 2`

Calculated property name
* `a -> (1+2)`
* `a -> ("text2 + " " + "more")`

Functions
* `myTime -> getFullYear()`
* `s -> substr(1,2)`

JavaScript string functions can also be used

```sql
    SELECT s->length FROM mytext
```

## JSON Objects

@ prefixes (like Objective-C NSObjects)
* @1
* @”string”
* @{a:1,b:2} or {a:1,b:2}
* @[1,2,3] – conflct with column names with spaces [My Column]

Three equal operators
* a = b like == in JavaScript
* a == b compare a.valueOf() and b.valueOf() – for dates
* a === b uses equalDeep() – for JSON objects

## JSON with expressions
```sqlCREATE TABLE one;
    INSERT INTO one VALUES @{b:1}, @{b:2}
    SELECT @{a:@[2014,(2014+1),(2014+b)]} FROM one
    [{a:[2014,2015,2015]}, {a:[2014,2015,2016]}]
```

## CREATE TABLE and insert JSON values

JSON table
```sql
    CREATE TABLE one;
    INSERT INTO one VALUES @{a:1}, @{b:2}, @{a:1,b:2}, @1, @”String”
```

JSON object
```sql
    CREATE TABLE two (a JSON);
    INSERT INTO one VALUES (1), (‘two’), (@{b:’three’}), @[‘F’,’O’,’U’,’R’]
```

## SELECT JSON
```sql
    SELECT * FROM one
    [{a:1}, {b:2}, {a:1,b:2}, 1, ”String”]

    SELECT a FROM one
    [{a:1}, {a:undefined}, {a:1}, {a:undefined},{a:undefined}]

    SELECT * FROM one WHERE a=1
    [{a:1},{a:1,b:2}]
```

Please note that you can avoid letting AlaSQL try to add extension to filenames by setting `autoExt:false` in the options given. 


See also

* [How to search deep nested JSON?](How to search deep nested-JSON)
* [How to traverse a complex JSON doc with javascript and extract named values?](How to traverse a complex JSON doc with javascript and extract named-values)
* [How to find all parents elements in a JSON file?](How to find all parents elements in a JSON-file)
* [How to recursive find and replace in multidimensional JavaScript object?](How to recursive find and replace in multidimensional JavaScript-object)


