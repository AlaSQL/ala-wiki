# Google Maps + AlaSQL

Pinpointing data on a map should be easy. Here is an example of AlaSQL used to prepare source data for Google Maps


```js

var csvUrl = 'https://cdn.rawgit.com/albertyw/avenews/master/old/data/average-latitude-longitude-countries.csv'

alasql(['SELECT * FROM CSV("'+csvUrl+'",{headers:true}) WHERE Latitude BETWEEN 0 AND 25']).then(function(res){
    var country = res[0];
    var mapOptions = { 
                        zoom : 3, center : new google.maps.LatLng(40, 0),
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

Play with this example [on jsFiddle](http://jsfiddle.net/7a772dt6/) 

Another live example of intergrating AlaSQL and Google Maps can be [seen here](http://alasql.org/demo/009geo)