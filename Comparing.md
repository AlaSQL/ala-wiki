# Comparing

In AlaSQL you can use standard comparing operators:
* = != (or <>)
* > >= < <=
* [BETWEEN](Between) / [NOT BETWEEN](Not-Between)

See the example:
```js
// Fill table with data
var person = [ 
    { name: 'bill' , sex:'M', income:50000 },
    { name: 'sara' , sex:'F', income:100000 },
    { name: 'larry' , sex:'M', income:90000 },
    { name: 'olga' , sex:'F', income:85000 },
];

// Do the query
var res1 = alasql("SELECT * FROM ? person WHERE income = 50000", [person]);
var res2 = alasql("SELECT * FROM ? person WHERE sex='F'", [person]);
```
You can try this example [in jsFiddle](http://jsfiddle.net/agershun/38hj2uwy/38/)