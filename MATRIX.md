# Keyword `MATRIX`

Result modifier for a `SELECT` 


Suggested syntax:
```sql
    MATRIX OF SELECT ...
```

Alternative syntax:
```sql
    SELECT MATRIX ...
```


Return data as an array of arrays (one array per row) instead of the default array of javascript objects. Row order is as requested in the select.


You can set query modifier for all SELECTs via:
```js
    alasql.options.modifier = 'MATRIX';
```

 

See also: [RECORDSET](Recordset), [VALUE](Value), [ROW](Row), [COLUMN](Column)