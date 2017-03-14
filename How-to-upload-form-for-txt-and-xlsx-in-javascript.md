# How to upload form for txt and xlsx in javascript?

Source: [StackOverflow.com](http://stackoverflow.com/questions/19211193/upload-form-for-txt-and-xlsx-in-javascript/27656225#27656225), [StackOverflow.com](http://stackoverflow.com/questions/5867675/how-can-you-read-excel-2007-file-xlsx-using-javascript-vbscript/27656359#27656359)

### Questions

1. I would like to make a form that allow user upload .txt and .xlsx file and write this file's contents in a div.I don't know if i should go server side to handle uploaded files.

2. I want to read the file uploaded by users on the client side and then do processing on them, instead of doing it on server-side. Is it possible read files and do manipulation using javascript on client side.

### Answer

You can read CSV or XLSX data with AlaSQL library. It uses [js-xlsx](js-xlsx) library.

If you read data from server:
```js
    alasql(['SELECT * FROM XLSX("data/myfile")']).then(function(data){
        // process data array
    });
```
If you are reading data from the browser:
```html
    <script src="alasql.min.js"></script>
    <script src="xlsx.core.min.js"></script>
    <p>Select CSV file to read:</p>
    <input id="readfile" type="file" onchange="loadFile(event)"/>
    <script>
        function loadFile(event) {
	        alasql('SELECT * FROM FILE(?,{headers:true})',[event],function(data){
		        // Process data here
	        });
         }
    </script>
```

AlaSQL automatically recognize file type by file extension.

See [this jsfiddle](http://jsfiddle.net/3ve90afo/) for a live example
