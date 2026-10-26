# Keyword `CREATE VIEW`

Syntax:
```sql
    CREATE VIEW viewid [(column, ...)] AS select
```

AlaSQL supports CREATE VIEW statement:

```js
    alasql('create table city (name string, population number); \
            create view bigcity (name) as select name from city where population > 1000000; \
            insert into city values ("Moscow",11500000), ("Berlin", 3500000), ("Yoshkar-Ola",250000)');

    alasql('insert into city values ("New York",16000000)');
```
Try this example [in jsFiddle](http://jsfiddle.net/0a1ovw1q/2/)

See also: [DROP VIEW](Drop-View)