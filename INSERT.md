# Keyword `INSERT`

Syntax:
```sql
    INSERT INTO table [(column1, column2...)] [VALUE[S]] valuePair1, valuePair2, ...;
    INSERT INTO table DEFAULT VALUES;
    INSERT INTO table SELECT ...;
```

[INSERT [VALUES]](Insert Values)
```js
    alasql('INSERT INTO city (name, population) VALUES ("Moscow",11500000), ("Kyiv",5000000)');
    alasql('INSERT INTO city VALUES {population:4000000, name:"Berlin"}');
    alasql('INSERT INTO city VALUES ?', [data]);
    alasql('INSERT INTO city VALUES ("Copenhagen",1000000)');
    alasql('INSERT INTO city VALUE ("Barcelona",1600000)');
    alasql('INSERT INTO city ("Paris",3500000)');
```

[INSERT DEFAULT VALUES](Insert Default-Values)
```js
    alasql('INSERT INTO city DEFAULT VALUES');
```

[INSERT SELECT](Insert-Select) (equivalent of SELECT INTO)
```js
    alasql('INSERT INTO city SELECT capital AS name FROM country GROUP BY capital;');
```

An `INSERT` statement will return the amount of rows inserted by the statment. 


----

See also: [INTO](Into), [SELECT INTO](Select-Into)