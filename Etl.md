# Extract, transform and load with AlaSQL

You can use AlaSQL and via the command line for ETL procedures. Install with 

    npm install -g alasql

##Examples    

### Load data from [CSV](Csv) file with headers
If you have a CSV file, you can process it directly in AlaSQL: 

```js
    alasql(['select * from csv("cities") where population > 100000 order by city']).then(function(data) {
         console.log(data);
    });
```

You can do the same query with the [[CLI]] interface and send file to stdout:
```bash
> alasql "select * from csv('cities') where population > 100000 order by city" >city.txt
```

### Prepare data from [XLSX](Xlsx) and XLS file
```js
    alasql(['select * from xlsx("./data/cities",{range:"A1:E100"})\
      where population > 100000 order by city']).then(function(data) {
         console.log(data);
    });
```


