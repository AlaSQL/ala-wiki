# Keyword `HAVING`

Filtering groups by expressions.

Syntax:
```sql
    SELECT ... GROUP BY gorup-expressions HAVING expression ...
```

For example, select countries with number of cities > 2:

```js
    var res = alasql('SELECT *, COUNT(*) AS cnt FROM City \
                GROUP BY Country \
                HAVING cnt > 2');
```

Expressions can contain aggregators, like below:

```js
    var res = alasql('SELECT * FROM City \
                GROUP BY Country \
                HAVING COUNT(*) > 2');
```

You can use aggregators in the ```HAVING``` clause like in this example:
```js
var groups = [{id:4, name:"abcd", id_group:"1"},
              {id:5, name:"efgh", id_group:"1"},
              {id:6, name:"ijkl", id_group:"1"},
              {id:4, name:"abcd", id_group:"2"},
              {id:7, name:"mnop", id_group:"2"}];
               
var res = alasql('select id_group, count(id) as cnt from ? where id in (4,7)\
group by id_group having count(id) = 2',[groups]);  
```
See this example in [jsFiddle](http://jsfiddle.net/5prbwtzy/2/)

See also: [WHERE](Where), [GROUP BY](Group-By)