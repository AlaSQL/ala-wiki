# Internal Structure

### How AlaSQL stores data?
* alasql.databases – list of all current databases in memory
* alasql.engines – list of all alasql available engines (like localStorage, IndexedDB)

### Database object properties
* tables - list of tables
* objects - list of document and graph objects

Classes
* [Database class](Database-Class)
* [Transaction class](Transaction-Class)
