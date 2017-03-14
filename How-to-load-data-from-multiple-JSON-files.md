# How to load data from multiple JSON files?

You can load data from multiple table in async mode with AlaSQL like below:
```js
    alasql(['SELECT * FROM JSON("a.json")',
            'SELECT * FROM JSON("b.json")',
            'SELECT * FROM JSON("c.json")'].then(function(res) {
             var a = res[0], b = res[1], b = res[2];
    });
```