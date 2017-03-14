# How to export HTML table to Excel?

### Answer

You can export table from HTML to Excel and skip some columns with AlaSQL and [js-xlsx](js-xlsx) libraries.

See the working example below or [in jsFiddle](http://jsfiddle.net/agershun/arkf83b9/):
```js
    function exportExcel() {
        alasql('SELECT * INTO XLSX("myinquires.xlsx",{headers:true}) \
                    FROM HTML("#MyInquires",{headers:true})');
    }
```
```html
    <script src="https://cdnjs.cloudflare.com/ajax/libs/alasql/0.3.7/alasql.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.9.2/xlsx.core.min.js"></script>
    <button onclick="exportExcel()">Export table to Excel</button>
    <p>Source table</p>
    <table id="MyInquires">
    	<thead><tr><th>#<th>Inquiry<th>Topic</thead>
    	<tbody>
    		<tr><td>1<td>WinPhone<td>Screen
    		<tr><td>2<td>iPhone<td>Keyboard
    		<tr><td>3<td>Android<td>Memory
    	</tbody>
    </table>
```
