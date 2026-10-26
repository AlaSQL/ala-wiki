## Keyword `CREATE TABLE`

Create table statement.

Syntax:
```sql
    CREATE TABLE tableid;
    CREATE TABLE tableid (
        column type constraints, ...
    );
```

```js
    alasql('CREATE TABLE star (  \
                one INT DEFAULT 100, \
                two STRING,\
                three BOOL PRIMARY KEY); \
    ');
    alasql('CREATE TABLE flight (flightNo INT, fromCity STRING, toCity STRING)');
```

### Tables without column declarations
For tables with unknown columns skip column definition part:
```js
    alasql('CREATE TABLE one');
    alasql('INSERT INTO one VALUES {a:1}');
```

### Columns data types
You can define data types for each column.

Also you can use columns without [data types](Data-Types):
```js
    alasql('CREATE DATABASE test252; USE test252;');
    alasql('CREATE TABLE sqlite_sequence(name,seq)');
    alasql('INSERT INTO sqlite_sequence VALUES (1,10)');
    alasql('INSERT INTO sqlite_sequence VALUES ("one","ten")');
    var res = alasql('SELECT * FROM sqlite_sequence');
```
returns:
```json
    [ { "name": 1, "seq": 10 }, { "name": "one", "seq": "ten" } ]
```

### Constraints

You can use the following types of constraints:
* [AUTO_INCREMENT](Identity), [AUTOINCREMENT](Identity), or [IDENTITY](Identity)
* [CHECK](Check)
* [PRIMARY KEY](Primary-Key)
* [FOREIGN KEY](Foreign-Key)

See also: [DROP TABLE](Drop-Table)