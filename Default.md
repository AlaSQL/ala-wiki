# DEFAULT

Syntax:
```sql
    CREATE TABLE tableid (
        columnid type DEFAULT expression
    );
```

AlaSQL supports column ```DEFAULT``` keyword:

```js
    alasql("CREATE TABLE test (a INT, \
            b INT DEFAULT 100)");
```

See also: [INSERT DEFAULT](Insert-Default)