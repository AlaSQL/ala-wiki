# Aggregators supported by AlaSQL

## SQL Standard

* SUM()
* AVG()
* COUNT()
* MAX()
* MIN()
* FIRST()
* LAST()

Examples:
```sql
    SELECT COUNT()
    SELECT COUNT(one)
    SELECT COUNT(*)
```

## Non-standard 
* AGGR() – operations on aggregated values
* ARRAY() – create array of values
* QUART() - 1st quartile 
* QUART2() - 2nd quartile
* QUART3() - 3rd quartile
* [User-defined aggregators](https://github.com/agershun/alasql/wiki/User-Defined-Functions)

Quartile aggregations are based on the European calculation. 

Example of AGGR() aggregator (here avg1 = avg2)
```sql
    SELECT SUM(a) AS sm, COUNT(*) AS cnt, \
           AGGR(sm/cnt) AS avg1, AVG(a) AS avg2 FROM data
```

