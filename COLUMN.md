# Keyword `COLUMN`



Syntax:
```sql
    -- Result modifier for a `SELECT`  
    COLUMN OF SELECT ...
    SELECT COLUMN ...

    -- Normal SQL
    ALTER TABLE table ADD COLUMN column type
    SELECT * REMOVE COLUMN (column | LIKE mask)
```


You can set query modifier for all SELECTs:
```js
    alasql.options.modifier = 'COLUMN';
```



See also: [ADD COLUMN](Add-Column), [REMOVE COLUMN](Remove-Column), [RECORDSET](Recordset), [VALUE](Value), [ROW](Row)