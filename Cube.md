# Keyword `CUBE`

AlaSQL supports CUBE() grouping options:
```js
var testData = [
    { Phase: "Phase 1", Step: "Step 1", Task: "Task 1", Val: 5 },
    { Phase: "Phase 1", Step: "Step 2", Task: "Task 2", Val: 20 },
    { Phase: "Phase 2", Step: "Step 1", Task: "Task 1", Val: 25 },
    { Phase: "Phase 2", Step: "Step 2", Task: "Task 2", Val: 40 }
];

res = alasql('SELECT Phase, Step, SUM(Val) AS Val FROM ? \
                  GROUP BY CUBE(Phase,Step)', [testData]);
```

Try this example [in jsFiddle](http://jsfiddle.net/agershun/1nccgs6n/2/)

See also: [ROLLUP](Rollup), [GROUPING SETS](Grouping-Sets), [GROUP BY](Group-By)