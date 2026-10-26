# Fluent Interface

_Experimental_

AlaSQL supports fluent like LINQ interface:

```js
    var res = alasql()
              .Where(function(x){x.Population>1000000})
              .OrderBy("Name")
              .exec(params);
```

## Supported functions
* [Select()](Select-Fluent)
* [From()](From-Fluent)
* [GroupBy()](GroupBy-Fluent)
* [Having()](Having-Fluent)
* [OrderBy()](OrderBy-Fluent)
* [Top()](Top-Fluent)



