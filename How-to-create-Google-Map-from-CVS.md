# How to create Google Map from CVS?

Source:[StackOverflow.com](http://stackoverflow.com/questions/9003404/google-maps-overlays-from-csv/27660997#27660997)

### Question

There is a CSV file with names and addresses. I need to plot markers on a Google Map using the data in the CSV file. How should I go about solving it?

### Answer

You can use AlaSQL library to load and parse CSV data from server or from desktop.

***FROM SERVER*** Here is an example of how to load data from CSV and pass it to Google Maps api (the full code and the result [you can see here](http://alasql.org/demo/009geo/)).
```js
    alasql(["SELECT * FROM CSV('https://cdn.rawgit.com/albertyw/avenews/master/old/data/average-latitude-longitude-countries.csv']).then(function(res){
    	var country = res[0];
        var mapOptions = { zoom : 3, center : new google.maps.LatLng(40, 0),
            mapTypeId : google.maps.MapTypeId.ROADMAP
        };
        var map = new google.maps.Map(document.getElementById('map-canvas'), mapOptions);
        for (i = 0; i < country.length; i++) {
            var opts = {
                strokeColor : '#000000',
                fillColor : ["red","green","blue","brown"][i%4],
                fillOpacity : 0.35,
                map : map,
                center : new google.maps.LatLng(country[i].Latitude,country[i].Longitude),
                radius : 100000
            };
            new google.maps.Circle(opts);
    });
```
***FROM DESKTOP*** If you want to upload data from desktop you can use the following code:
```html
     <script src="alasql.min.js"></script>
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
The working example how to upload file [is here](http://alasql.org/demo/008file/).
