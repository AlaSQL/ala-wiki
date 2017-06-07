AlaSQL has XLSXML() export function with coloring functionality. The correct extension for the files is `.xls`.

```js
var data = [{city:"London",population:5000000}, 
    {city:"Moscow",population:12000000},
    {city:"Mexico",population:20000000}, 
    {city:"New York",population:20000000}, 
];

var opts = {
  headers:true, 
  column: {style:{Font:{Bold:"1"}}},
  rows: {1:{style:{Font:{Color:"#FF0077"}}}},
  cells: {1:{1:{
    style: {Font:{Color:"#00FFFF"}}
  }}}
};
alasql('SELECT * INTO XLSXML("restest280b.xls",?) FROM ?',[opts,data]);
```

Test this example in https://jsfiddle.net/vL4tsaef/1/

Here you can define style for any column, row, or cell in the sheet.

To write special character (like `& , _ \`) to the sheet name (sheetid) you need to escape in xml format. Example: http://jsfiddle.net/ry8fq0dL/125/