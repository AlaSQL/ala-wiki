# Keyword `JOIN`

Syntax:
```sql
    SELECT ... FROM table1 joint-type JOIN table2 (USING|ON)...
```

## Join Types
Supported join types:
* [INNER JOIN](Inner-Join)
* [LEFT [OUTER] JOIN](Left Join)
* [RIGHT [OUTER] JOIN](Right Join)
* [[FULL] OUTER JOIN](Outer Join)
* [ANTI JOIN](Anti-Join)
* [SEMI JOIN](Semi-Join)
* [CROSS JOIN](Cross-Join)
* [NATURAL JOIN](Natural-Join)

For example:
```js
    alasql('SELECT * FROM Cities JOIN Countries');
```

### JOIN USING clause
```js
    alasql('SELECT city.*, country.* FROM city \
                JOIN country USING countryid');
    alasql('SELECT * FROM Cities JOIN Countries USING Country');
```

### JOIN ON clause
```js
    alasql('SELECT city.*, country.* FROM city \
                JOIN country ON city.countryid = country.countryid');
    alasql('SELECT * FROM Cities JOIN Countries ON Citites.Country = Countries.Country');
```

### UNING and ON

Actually AlaSQL converts internally to the same execution plan, like in this example:

JOIN USING works fine in [this example](http://jsfiddle.net/agershun/na64p95k/1/)
```js
      var data = { COLORS: [[1,"red"],[2,"yellow"],[3,"orange"]],            
       "FRUITS":[[1,"apple"],[2,"banana"],[3,"orange"]]};

     data.NEW_FRUITS = alasql('SELECT MATRIX COLORS.[0], COLORS.[1], \
     FRUITS.[1] AS [2] FROM ? AS COLORS JOIN ? AS FRUITS USING [0]',
     [data.COLORS, data.FRUITS]);
 
```

With using JOIN ON in [this example](http://jsfiddle.net/agershun/Lxgfduov/):

```js
   var data = { COLORS: [[1,"red"],[2,"yellow"],[3,"orange"]],            
       "FRUITS":[[1,"apple"],[2,"banana"],[3,"orange"]]};

    data.NEW_FRUITS = alasql('SELECT MATRIX COLORS.[0], COLORS.[1], FRUITS.[1] AS [2] \
    FROM ? AS COLORS JOIN ? AS FRUITS ON COLORS.[0] = FRUITS.[0]',
    [data.COLORS,     data.FRUITS]);
```

See the expected results in [Join On Join](Join On-Join) page.

See also: [SELECT](Select), [USING](Using), [ON](On), [APPLY](Apply)