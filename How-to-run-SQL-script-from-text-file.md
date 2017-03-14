# How to run SQL script from text file?

### Question
I have all my SQL statements in a text file. How to run it in AlaSQL?

### Answer
You can use [[SOURCE]] statement:
```js
    alasql('SOURCE "myfile.sql"');
```

Please not that accessing files in a browser should be done async:
```js
    alasql(['SOURCE "myfile.sql"']).then(function(){ 
    	... 
    });
```