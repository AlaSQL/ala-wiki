# Keyword `GROUP BY`

Syntax:
```sql
    SELECT ... GROUP BY expression, expression...
    SELECT ... GROUP BY CUBE(expression,...) | ROLLUP(expression,...) | GROUPING SETS(expression,...)  
```
#### Grouping by columns
```js
    var res = alasql('SELECT * FROM City GROUP BY Contient, Country');
```

When selecting `*` the fields not mentioned in the `GROUP BY` will be given the [`FIRST(fieldName)`](FIRST) value: the value from the very first record in the group from the original data array. Please notice that the value therefore depends solely on the order of the records.

#### Grouping by expressions

```js
    var res = alasql('SELECT a%2 as isOdd, count(*) as `count` FROM Nums GROUP BY a%2');
```

Will tell you how many a's are odd and how many are even. [See jsFiddle](http://jsfiddle.net/wm2uvx9e/)

The example:
```js
    alasql('SELECT projects, FIRST(duration) AS duration, \
        FIRST([path]) AS [path], FIRST(application) AS application  \
        FROM json("timing_output") \
        GROUP BY projects, duration, [path], application \
        ORDER BY duration DESC',[],function(res){
          console.log(res);
    });
```
Try this example in [jsFiddle](http://jsfiddle.net/j39agf7c/1/)

## Grouping functions
* [CUBE()](Cube)
* [ROLLUP()](Rollup)
* [GROUPING SETS()](Grouping-Sets)

```js
    alasql('SELECT * FROM City GROUP BY ROLLUP(Continent, Country)');
```
See [jsFiddle example](http://jsfiddle.net/agershun/1nccgs6n/2/) for ROLLUP(), CUBE(), and GROUPING SETS().

See also: [SELECT](Select), [HAVING](Having), [CUBE](Cube), [ROLLUP](Rollup), [GROUPING SETS](Grouping-Sets)
