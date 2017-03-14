# How to import and export Excel files to javascript array?

Source: [StackOverflow.com](http://stackoverflow.com/questions/27511629/importing-and-exporting-excel-files-to-javascript-array/27616508#27616508)

### Question

I'm currently looking for a fast and efficient way to import an Excel file into a javascript array, and export it also. I also need a way to do the same thing, but the opposite way. 

### Answer

For import:
```js
    alasql('SELECT * FROM XLSX("srcfileName")'].then(function(data){
        console.log(data);
    });
```
For export:
```js
    var data = [{a:!,b:10},{a:2,b:20}];
    alasql('SELECT * INTO XLSX("myfileName") FROM ?',[data]);
```

Import and export with interim data processing:
```js
    alasql('SELECT * \
                INTO XLSX("myfile.xlsx",{headers:true}) \
                FROM XLSX("srcfile.xlsx",{headers:true}) \
                WHERE Age > 20 \
                GROUP BY LastName \
                HAVING COUNT(*) > 2 \
                ORDER BY LastName, FirstName');
```