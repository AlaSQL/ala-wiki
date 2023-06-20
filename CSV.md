# Keyword `CSV`

AlaSQL can import from and export to CSV (comma-separated values) format.

Syntax:
```sql
    SELECT column INTO CSV(filename,options) FROM tableid;
    SELECT column FROM CSV(filename,options) ;
```

Please note that when interacting with files AlaSQL [will run async](async). We strongly recommend you to [use the promise notation](promise) instead of the simple notation: [`alasql(sql, params, function(data) { console.log(data) })`](async)


### Import CSV data
```js
    alasql.promise('SELECT * FROM CSV("my.csv", {headers:false})')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```
You can try this example [in jsFiddle](http://jsfiddle.net/agershun/efmhcnu8/1/)

You can also give the full content of a CSV file as a string instead of the path. 

You can specify delimiters and quote characters:
```js
    alasql.promise('SELECT * FROM CSV("my.csv", {headers:false, quote:"\'",separator:","})')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```

Example on how to change the seperator only
```js
   alasql.promise('SELECT * FROM CSV("a.csv",{separator:";"})')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```

### Export to CSV data
```js
    alasql.promise('SELECT * INTO CSV("my.csv", {headers:false}) FROM ?',[data])
            .then(function(){
                 console.log('Data saved');
            }).catch(function(err){
                 console.log('Error:', err);
            });;
```


## Options

For CSV you can set the following options

- **header** is default `true`. If set to `false` the first row in the CSV file will contain data instead of the column names
- **utf8Bom** default depends on header. If headers will be included it will be default `true`. If headers not included it will be default `false`. If `true` BOM will be added to the CSV file (useful in some cases with excel)
- **separator** is default `;` and can be set to any string used as a seperator
- **quote** is default `"` and can be set to any string used to quote strings
- **raw** is default `false` and can be set to true if you want all data returned as the raw string (so no conversion of numbers)

Please note that default seperator is `;` and not `,` as specified by the [RFC](https://www.ietf.org/rfc/rfc4180.txt). The reason is that [Excel cant always handle ','](https://kb.paessler.com/en/topic/2293-i-have-trouble-opening-csv-files-with-microsoft-excel-is-there-a-quick-way-to-fix-this#reply-5193). As Excel usage is such a big use case for the library we rather bother people who can't handle the incorrect `.csv` file with adding the parameter {seperator:','} than getting questions from all the people who cant make the lib "work" with Excel. 

See also: [TAB](Tab), [TSV](Tsv), [XLSX](Xlsx), [JSON](Json)

