# Angular.js + AlaSQL


You can use AlaSQL together with Angular.js framework. Please include the file normally and not via requireJS. Please include alasql before requireJS to avoid issue of "Mismatched anonymous define() module". This issue is with requireJS.

```js
    $scope.exportData = function () {
        alasql('SELECT * INTO XLSX("john.xlsx",{headers:true}) FROM ?',[$scope.items]);
    };
```
See [simple example in jsFiddle](http://jsfiddle.net/agershun/00nfeq12/).

Another example: [Calculating average of array](http://jsfiddle.net/agershun/she06Lq3/2/)


## In more detail

If AlaSQL recognize Angular.js it removes ```$$hashKey``` artefacts from the exporting arrays.

To remove other artefact fields you can use [REMOVE COLUMNS](Remove Columns) clause.

(Source: [AlaSQL Group](https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!msg/alasql/w9uavEdVHAU/k4KXf2Pv3WoJ) by **Built with AngularJS Application**)

For example, you can integrate these libraries it for import or export data files from MS Excel.

### Export file to Excel 
HTML:
```html
    <button ng-if="$root.appInfo.model.rows"     // show excel icon only if there are rows in the grid 
        class="btn"ng-click="$root.exportData()">
    </button> 
```
Controller:
```
    $rootScope.exportData = function () {
        alasql('SELECT * INTO XLSX("list.xlsx",{headers:true}) FROM ?', 
              [$rootScope.appInfo.model.rows]);   
    };
```

Codepen example: http://codepen.io/DickSwart/pen/wWPYpX/

### Import data from file in client computer

Unfortunately, we cannot use ```ng-change``` because the input needs to be bound (```ng-model```), but it seems that ```type=file``` inputs are not supported for binding in Angular.js, so we can switch to ```ng-mouseleave``` and it worked, though we had to check in the function that a file had been chosen.

HTML:
```html
    <input type="file" ng-mouseleave="loadFile($event)" />
```
Controller:
```
    $rootScope.loadFile = function (event) {
        if (event.fromElement.files.length==0) {
            return(false);   // leave in case no file was chosen
        };
        alasql('SELECT * FROM FILE(?,{headers:true})', [event], function (data) {
            $rootScope.eData = data;     //  eData contains the JSON representation of the Excel sheet rows
        }); 
    };
```

Play with this example: http://jsfiddle.net/vxjgnmxa/ (only chrome)

For firefox support, please check out https://github.com/agershun/alasql/tree/develop/examples/angular/import-export-excel

For Angular cli: have a look at https://github.com/agershun/alasql/issues/738#issuecomment-277266095

### NG2

Steps for a working AlaSQL configuration inside an NG2 project are:
1. **npm install alasql --save**
2. optional for XLSX export: **npm install xlsx --save** 
3. add the javascript dependencies inside the **.angular-cli.json** file of your project
```
"scripts": [
    "../node_modules/alasql/dist/alasql.min.js",
    "../node_modules/xlsx/dist/xlsx.core.min.js"
],
```
4. next import into one of your components where you woudl like to use the alasql function (not inside app-module.ts) the AlaSQL dependency. 
`import * as alaSQLSpace from 'alasql';` 
5. and if you would like to test your code, you can add this test block from [jsfiddle:](http://jsfiddle.net/gd7jex9s/) into your component.
```
public testAlaSQLExcelExport(): void {
   var data1 = [{ a: 1, b: 10 }, { a: 2, b: 20 }];
   var data2 = [{ a: 100, b: 10 }, { a: 200, b: 20 }];
   var opts = [{ sheetid: 'Good', header: true }, { sheetid: 'Two', header: false }];
   var res = alasql('SELECT INTO XLSX("MyAwesomeData.xlsx",?) FROM ?', [opts, [data1, data2]]);
}
```
6. now if you run **ng serve** the project will compile without any errors or warnings and if the **testAlaSQLExcelExport()** function is used you can see that the excel file will be exported inside your browser.