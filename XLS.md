# Excel 2003 files: .XLS

AlaSQL can export data in Excel 2003 format (.xls) with coloring of cells.

Please know that we recommend exporting to [".xlsx"](XLSX) instead of ".xls" as Microsoft has started [refusing to open files in the old format](http://www.infoworld.com/article/3098898/microsoft-windows/excel-refusing-to-open-files-blame-the-kb-3115322-3115262-security-updates.html).


```js
    var opts = {
      headers: true,
      sheetid: 'My Birds',
      style:"background:#00ff00",
      columns: [
        {columnid:'a',title:'Albatroses',
          style:'background:red;font-size:20px',
          cell:{style:'background:blue'}
        },
        {columnid:'b',title:'Bird',cell:{
          style:function(value,sheet,row,column,rowidx,columnidx){
            return 'background'+(value==10?'brown':'white')
        }}},
        { 
          columnid: 'b', cell:{value:function(value){ return value * value}}
        }
      ]
    };

    var res = alasql('SELECT * INTO XLS("restest257a",?) FROM ?',[opts,data]); 

```
Please, see the example with advanced color syntax [in jsFiddle](https://jsfiddle.net/dsn9xobr/).

You can pass the object as a Blob:

    alasql('SELECT * FROM XLS(?,{headers:true}',[myblob]);


To read `.xls` files, please include the `xlsx` lib from https://cdnjs.com/libraries/xlsx


If you need Excel 2007 files please check out [[XLSX]]