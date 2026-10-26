# Keyword `NEW`

The AlaSQL ```NEW``` operator is the same as JavaScript ```new``` operator.

You need to register JavaScript class with ```alasql.fn``` variable:
```js
    alasql.fn.MyClass = function() {};
    alasql('SELECT NEW MyClass()');
```

See also: [User-defined functions](User-defined-functions)