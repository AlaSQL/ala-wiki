# How to hide HTML columns when exporting to Excel?

Source: [StackOverflow.com](http://stackoverflow.com/questions/14798544/hide-html-columns-when-exporting-to-excel/27664947#27664947)

### Question

I'm trying to export HTML table using header output in php. I'm using jquery to hide the columns by checkbox event. My jquery code to unhide and hide column is:
```js
    $('.col').css('display','table-cell');
    $('.col').css('display','none');
```
When I export my html table with hidden columns, the hidden columns still appears.
I want to hide those columns while exporting to Excel.

### Answer

You can export table from HTML to Excel and skip some columns with AlaSQL and [js-xlsx](js-xlsx) libraries.

To skip unnecessary columns you can use "skipdisplaynone" parameter (like in the example below) or list columns you need in the SELECT statement instead "*".

To skip unnecessary columns you can use "skipdisplaynone" parameter (like in the example below) or list columns you need in the SELECT statement instead "*".
```js
    alasql('SELECT * FROM HTML("#table", {headers:true, skipdisplaynone:true})');
    alasql('SELECT Name FROM HTML("#table", {headers:true})');
```
See the working example below with table, where column "Name" is hidden [in jsFiddle](http://jsfiddle.net/agershun/8rdL8m3L/1/):
```js
    function exportExcel() {
        alasql('SELECT * INTO XLSX("table.xlsx",{headers:true}) \
                    FROM HTML("#table",{headers:true,skipdisplaynone:true})');
    }
```
```html
    <script src="https://cdnjs.cloudflare.com/ajax/libs/alasql/0.3.7/alasql.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.9.2/xlsx.core.min.js"></script>
    <button onclick="exportExcel()">Export table to Excel</button>
    <p>Source table</p>
    <table  id="table" title="banner"  border="1" align="center" >
        <thead>
             <tr><th>ID</th><th style="display:none">Name</th><th>Month</th><th>Savings</th></tr>
        </thead>
        <tbody>
             <tr><td>101</td><td style="display:none">Ramesh</td><td>January</td><td>$100</td></tr>
             <tr><td>102</td><td style="display:none">Ram</td><td>Feb</td><td>$200</td></tr>
             <tr><td>103</td><td style="display:none">Ramna</td><td>Mar</td><td>$300</td></tr>
       </tbody>
    </table>
```
