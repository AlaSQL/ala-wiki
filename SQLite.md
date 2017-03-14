# SQLite

AlaSQL can read from SQLite files if the [SQL.js](https://github.com/kripken/sql.js/) is included. When the library is included you can attach a SQLite db file to AlaSQL like in the example below:

```html
    <script src="alasql.js"></script>
    <script src="sql.js"></script>
    <script>
        alasql(['ATTACH SQLITE DATABASE Chinook("Chinook_Sqlite.sqlite");\
            USE Chinook; \
            SELECT * FROM Genre'].then(function(res){
                console.log("Genres:",res.pop());
        });
    </script>
```

You can use this feature for advanced [ETL](Etl) operations. For example, you can easily open [SQLite](Sqlite) file and store it to [IndexedDB](IndexedDB) database:
```
    alasql(['ATTACH SQLITE DATABASE geo("geo.sqlite") AS geo1; \
               ATTACH INDEXEDDB DATABASE geo AS geo2; \
              SELECT * INTO geo2.cities FROM geo1.cities']);
``` 

Please note that it's not yet possible to update the SQLite db file from AlaSQL.