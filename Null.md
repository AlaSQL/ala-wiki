# Keyword `NULL`

AlaSQL supports ```NULL``` keyword.

Syntax:
```sql
    NULL
```


### JavaScript emulation

AlaSQL uses ```undefined``` value to emulate SQL ```NULL``` constant instead of ```null```. 

### NULL Constraint

You can set ```NULL``` column constraint. In this example the ```partname``` column can accept ```NULL``` values.
```sql
CREATE TABLE dbo.Parts (
  partid   INT         NOT NULL PRIMARY KEY,
  partname VARCHAR(25) NULL
);
```

----

You can use `NULLS LAST` and `NULLS FIRST` in your sort order to determine the sorting

    SELECT a, b FROM ? ORDER BY a ASC NULLS FIRST, b ASC NULLS LAST

See also: [ISNULL](Isnull), [NOT NULL](Not Null)