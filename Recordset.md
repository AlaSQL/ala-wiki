# Keyword `RECORDSET`

Suggested Syntax:
```sql
    RECORDSET OF SELECT ...
```

Alternative syntax:
```sql
    SELECT RECORDSET...
```


Usually AlaSQL returns array of records (JavaScript objects), but you can modify SELECT statement to return an object with both data (as normal select) and data about the order of the rows in the select.



AlaSQL modifier for SELECT queries.
```sql
    SET @data = @[{a:1,b:10},{a:2,b:20}];
    SELECT a, b FROM @data;
    -- returns array of objects [{a:1,b:10},{a:2,b:20}]

    RECORDSET OF SELECT a, b FROM @data;
    -- returns array of objects 
    -- {data:[{a:1,b:10},{a:2,b:20}] , columns:[{columnid:'a'},{columnid:'b'}]}
```

You can change also query modifier with AlaSQL options:
```js
    alasql.options.modifier = 'RECORDSET';
```
By default, all nestes subqueries returns data as Recordset.


See also: [VALUE](Value), [MATRIX](Matrix), [COLUMN](Column), [ROW](Row)