# How to upload and parse CSV file from server and from desktop?

You can use [AlaSQL][1] library to load and parse CSV data from server or from desktop.

####From Server 
You can and parse data with CSV() function:
```js
    alasql(['SELECT * FROM CSV("mydata")']).then(function(data) {
        // Use data
    });
```

####From Desktop
If you want to upload data from desktop you can use the following code:
```js
     <script src="alasql.min.js"></script>
     <p>Select CSV file to read:</p>
     <input id="readfile" type="file" onchange="loadFile(event)"/>
     <script>
         function loadFile(event) {
            alasql(['SELECT * FROM FILE(?,{headers:true})',[event]]).then(function(data){
            	// Process data here
            });
         }
     </script>
```
See [this jsfiddle](http://jsfiddle.net/3ve90afo/) for a live example

See also [[How to upload form for txt and xlsx in javascript]]