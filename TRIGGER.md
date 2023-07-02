# Keyword `TRIGGER`

Syntax:
```sql
    CREATE TRIGGER triggerName (BEFORE|AFTER|INSTEAD OF) (INSERT|DELETE|UPDATE) ON tableName (Statement|Function)
```

Example A
```js
    alasql.fn.verify = function(r) {
         if(r.n == 42) return false; // Do not insert on this number 
    };
    alasql('CREATE TRIGGER mytrigger BEFORE INSERT ON mytable verify');
```

Example B
```js
    alasql.fn.onchange = function(r) {
        if(r.a == 123) console.log('Observable event!');
    };;
    alasql('CREATE TABLE one (a INT)');
    alasql('CREATE TRIGGER two BEFORE INSERT ON one CALL onchange()');
    alasql('INSERT INTO one VALUES (123)');  // This will fire onchange()
```


Limitations:
* No `INSTEAD OF DELETE` 
* `BEFORE/AFTER DELETE` can not prevent record from deletion 
* Triggers do not works for `DELETE FROM` mytable without `WHEN` clause
* Some issues have been reported on indexedDB. Please report any new issues. 

