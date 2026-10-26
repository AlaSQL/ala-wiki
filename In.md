# IN

Syntax:
```sql
    expression IN array
```

AlaSQL supports ```IN``` operatior:
```sql
    SELECT a FROM one WHERE b IN (1,2,3)
    SELECT a FROM one WHERE b IN (SELECT b FROM two)
    SELECT a FROM one WHERE b IN ?
```
### In the expression:
```js
    expression IN @(expression)
```
like:
```sql
    10 IN @(?)
    @a IN @(@b)
    20 IN @(@[10,20,30])
```
See the example [in jsFiddle](http://jsfiddle.net/agershun/q7pz7w60/1/)

See also: [NOT IN](Not-In), [EXISTS](Exists)