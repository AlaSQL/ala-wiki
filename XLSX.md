# `.XLSX` - Excel 2007 

To work with `.xlsx` files, please include `xlsx` from https://cdnjs.com/libraries/xlsx

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/X.Y.Z/xlsx.core.min.js"></script>
```

Please note that when interacting with files AlaSQL [will run async](async). We strongly recommend you to [use the promise notation](promise).


### Read from XLSX

```js
    alasql.promise('select City, Population from xlsx("cities.xlsx") where Population > 100000')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```

### Save data to XLSX

```js

    alasql.promise('SELECT * INTO XLSX("restest280b.xlsx") FROM ?', [data])
            .then(function(data){
                 console.log('Data saved');
            }).catch(function(err){
                 console.log('Error:', err);
            });
```

To store data in multiple sheets have a look at http://jsfiddle.net/np3pea44/
		
### Options

XLSX() function supports the following options:

#### sheetid
Sheet name:
```js
    alasql.promise('select * from xlsx("cities.xlsx",{sheetid:"Sheet2"}')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```
By default AlaSQL read data from sheet "Sheet1".

#### Range
Cells range:
```js
    alasql.promise('select * from xlsx("cities.xlsx",{range:"A1:D100"}')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```
By default AlaSQL read all data in the sheet.

#### headers
Read headers from data range (true/false):
```js
    alasql.promise('select * from xlsx("cities.xlsx",{headers:true}')
            .then(function(data){
                 console.log(data);
            }).catch(function(err){
                 console.log('Error:', err);
            });
```
By default AlaSQL headers are set to `true`


### Example

```js
    var mystyle = {
      headers:true, 
      column: {style:{Font:{Bold:"1"}}},
      rows: {1:{style:{Font:{Color:"#FF0077"}}}},
      cells: {1:{1:{
        style: {Font:{Color:"#00FFFF"}}
      }}}
    };
    alasql.promise('SELECT * INTO XLSXML("restest280b.xls",?) FROM ?',[mystyle,data])
            .then(function(data){
                 console.log('Data saved');
            }).catch(function(err){
                 console.log('Error:', err);
            });
```
See the working example in [jsFiddle](http://jsfiddle.net/95j0txwx/7/)

Please note that you can avoid letting AlaSQL try to add extension to filenames by setting `autoExt:false` in the option. 

You can also pass the file as a Blob:

    alasql('SELECT * FROM XLSX(?)',[myblobData]);		

---

AlaSQL uses js-xlsx library to read and export Excel files.

js-xlsx at Github: https://github.com/SheetJS/js-xlsx



----

By default AlaSQL look through first 10 records to collect infomation about all columns. You can change this flag to be sure that AlaSQL collect information about all columns in all records (it may take a time for large recordsets).

    alasql.options.columnlookup = 10;

----

To read blank column values from xls,xlsx and csv you can use this notation for column names [0],[1],[2] like:

    SELECT [0],[2] FROM XLS('filename.xls') WHERE [3] > 100

----

Problem with dates when you read your file? Have a look at [this comment](https://github.com/agershun/alasql/issues/395#issuecomment-290392777)

----

Uploading files directly into AlaSQL? Have a look at https://github.com/agershun/alasql/issues/971#issuecomment-360121191

----

If you need Excel 2003 files please check out: [[XLS]]