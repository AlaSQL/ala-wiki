# Formatting Dates with Moment.js

You can use [Moment.js](http://momentjs.com/) library to format dates:
```js
    moment.locale('fr'); // Set French locale for moment.js
    alasql.fn.moment = moment; // Set moment() function available to AlaSQL

    var data = [{d:new Date()},{d:"2013-02-14"}];
    var res = alasql('SELECT moment(d)->[add](1,-"days")->calendar() as [When?]\
            FROM ?',[data]);
```

See the full example [in jsFiddle](http://jsfiddle.net/agershun/aapmn9h1/2/)