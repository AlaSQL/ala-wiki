# How to export JavaScript Array of Filtered HTML Table data to MS Excel or CSV?

Source:[StackOverflow.com](http://stackoverflow.com/questions/6846810/export-javascript-array-of-filtered-html-table-data-to-ms-excel-or-csv/27661435#27661435)

### Question

How do I get the JavaScript array into an Excel or CSV file? Again, this will be accessed only by IE so activeX objects and controls are acceptable. Also I should probably note that I cannot use server-side technologies so please limit your responses to the confines of HTML, javascript and activeX

### Answer

You can use AlaSQL with [js-xlsx](js-xlsx) library to export data locally in XLSX file format.

Below you can see a simple working example how to export data to XLSX format.

```html
    <script src="https://cdnjs.cloudflare.com/ajax/libs/alasql/0.3.7/alasql.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.9.2/xlsx.core.min.js"></script>
    <button onclick="exportData()">Export data to Excel</button>
```
```js
    var data = [{city:"Minsk",population:100000}, {city:"Riga",population:200000}];

    function exportData() {
        alasql("SELECT * INTO XLSX('cities.xlsx',{headers:true}) FROM ? ",[data]);
    }
```

Try the working example [at jsFiddle](http://jsfiddle.net/agershun/0xgfjcre/1/)