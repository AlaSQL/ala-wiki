# Keyword `CUBE`

## Introduction
The `CUBE` operation in AlaSQL is an extension of the `GROUP BY` clause that allows you to generate multiple grouping sets in a single query. It's particularly useful for generating subtotals and grand totals in multidimensional data analysis, such as in OLAP (Online Analytical Processing) applications.

## Syntax
```sql
SELECT column1, column2, ..., aggregate_function(column)
FROM table
GROUP BY CUBE(column1, column2, ...)
```

## Explanation
The `CUBE` operation generates all possible combinations of the specified dimensions. For `n` dimensions, it produces 2^n grouping sets. This includes:
- The grand total
- Subtotals for all combinations of dimensions
- Individual totals for each dimension

## Examples

### Basic CUBE Operation
```js
var testData = [
    { Phase: "Phase 1", Step: "Step 1", Task: "Task 1", Val: 5 },
    { Phase: "Phase 1", Step: "Step 2", Task: "Task 2", Val: 20 },
    { Phase: "Phase 2", Step: "Step 1", Task: "Task 1", Val: 25 },
    { Phase: "Phase 2", Step: "Step 2", Task: "Task 2", Val: 40 }
];
var res = alasql('SELECT Phase, Step, SUM(Val) AS Val FROM ? \
                  GROUP BY CUBE(Phase,Step)', [testData]);
```

Result:
```js
[
  { Phase: 'Phase 1', Step: 'Step 1', Val: 5 },
  { Phase: 'Phase 1', Step: 'Step 2', Val: 20 },
  { Phase: 'Phase 1', Step: null, Val: 25 },
  { Phase: 'Phase 2', Step: 'Step 1', Val: 25 },
  { Phase: 'Phase 2', Step: 'Step 2', Val: 40 },
  { Phase: 'Phase 2', Step: null, Val: 65 },
  { Phase: null, Step: 'Step 1', Val: 30 },
  { Phase: null, Step: 'Step 2', Val: 60 },
  { Phase: null, Step: null, Val: 90 }
]
```

In this result:
- Rows with both Phase and Step represent individual groupings
- Rows with Phase but null Step represent subtotals for each Phase
- Rows with Step but null Phase represent subtotals for each Step
- The last row with both null represents the grand total

### CUBE with More Dimensions
```js
var res = alasql('SELECT Phase, Step, Task, SUM(Val) AS Val FROM ? \
                  GROUP BY CUBE(Phase, Step, Task)', [testData]);
```

This query will generate 2^3 = 8 grouping sets, including all possible combinations of Phase, Step, and Task.

## Comparison with ROLLUP
While `CUBE` generates all possible combinations of dimensions, `ROLLUP` generates a subset of those combinations. `ROLLUP` is hierarchical, moving from the most detailed level to the grand total.

For example, `ROLLUP(Phase, Step)` would produce:
- (Phase, Step)
- (Phase)
- ()

Whereas `CUBE(Phase, Step)` produces:
- (Phase, Step)
- (Phase)
- (Step)
- ()

## Performance Considerations
- `CUBE` can generate a large number of rows, especially with many dimensions. Use it judiciously to avoid performance issues with large datasets.
- Consider using `GROUPING SETS` for more control over which specific combinations are generated.

## Try it out
You can try the basic CUBE example [in jsFiddle](http://jsfiddle.net/agershun/1nccgs6n/2/).

## See Also
- [ROLLUP](Rollup)
- [GROUPING SETS](Grouping Sets)
- [GROUP BY](Group By)
