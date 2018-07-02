# Keyword `SEARCH`

AlaSQL ```SEARCH``` operator is designed to traverse over JSON objects and graphs and is inspired by the [OrientDB graph search](https://github.com/agershun/alasql/issues/131#issuecomment-94413228)

Syntax:
```sql
    SEARCH selectors [FROM (table|object)]
```

You can use it with graphs:
```js
    var res = alasql('SEARCH / "Harry" PATH("Roger") VERTEX name');
```
or with JSON files:
```js
   var catalog = { 
     Europe: {
       fruits: [
         {fruit:'Apple'},
         {fruit:'Peach'},          
       ]
     },
     Asia: {
         fruit:'Pineapple'          
     },
     Africa: {
         fruit:'Banana'          
     }
   };

    var res = alasql('SEARCH Europe FROM ?',[catalog]);
    // [{fruits: [
    //    {fruit:'Apple'},
    //    {fruit:'Peach'},          
    //  ]}]);

    var res = alasql('SEARCH /fruits/ FROM ?',[catalog]);
    // [{fruit:'Apple'}, {fruit:'Peach'}]

    var res = alasql('SEARCH /fruits/fruit FROM ?',[catalog]);
    // ['Apple','Peach']

    var res = alasql('SEARCH /fruits/WHERE(fruit="Apple") FROM ?',[catalog]);
    // [{fruit:'Apple'}]

    var res = alasql('SEARCH ///WHERE(fruit="Apple") FROM ?',[catalog]);
    // [{fruit:'Apple'}]
```

Have a look at [[RETURN]] to modify the output when wanting to finetune `SEARCH` outputs 

### More relevant example:
```js
var alasql = require('alasql');

var data = [
	{
		teamname:'Alpha',
		members: [
			{
				membername:'Andrey',
				categories: ['JavaScript','C++']
			},
			{
				membername:'Mathias',
				categories: ['JavaScript','PHP']
			},
		]
	},
	{
		teamname:'Beta',
		members: [
			{
				membername:'Ole',
				categories: ['JavaScript']
			}
		]
	},
];

var res = alasql('SEARCH / AS @team \
		members / AS @member \
		categories / AS @category  \
		RETURN(@team->teamname AS team, @member->membername AS member, @category AS category) \
		FROM ?',[data]);
console.log(res);
```
returns
```js
[ { team: 'Alpha', member: 'Andrey', category: 'JavaScript' },
  { team: 'Alpha', member: 'Andrey', category: 'C++' },
  { team: 'Alpha', member: 'Mathias', category: 'JavaScript' },
  { team: 'Alpha', member: 'Mathias', category: 'Java' },
  { team: 'Beta', member: 'Ole', category: 'JavaScript' } ]
```

Here:
* `SEARCH` - search keyword
* `/` - walk over all members of array
* `AS @team` - save result into temporary variable `team`
* ` members` - take member property of previous result
* `/` - walk over all members of members array
* `AS @member` - save result into temporary variable `member`
* ` categories` - take category property of previous result
* `/`- walk over categories array
* `RETURN(...)` - pseudo-function to create result record
* `RETURN(@team->teamname AS team,...)` - take temporary variable 'team', take its teamname property and store it as team property of result object
* `FROM ?` - standard source from array clause
* `alasql('...',[data])` - take source data from `data` array

### Other examples of ```SEARCH``` operator:
* [How to parse a Json with array and objects and export the data into Excel file](How to parse a Json with array and objects and export the data into Excel file)

The following testfiles has examples on how to use `SEARCH`: , [test289.js](https://github.com/agershun/alasql/blob/develop/test/test289.js), [test292.js](https://github.com/agershun/alasql/blob/develop/test/test292.js), [test300.js](https://github.com/agershun/alasql/blob/develop/test/test300.js), [test301.js](https://github.com/agershun/alasql/blob/develop/test/test301.js), [test302.js](https://github.com/agershun/alasql/blob/develop/test/test302.js), [test303.js](https://github.com/agershun/alasql/blob/develop/test/test303.js), [test304.js](https://github.com/agershun/alasql/blob/develop/test/test304.js), [test305.js](https://github.com/agershun/alasql/blob/develop/test/test305.js), [test306.js](https://github.com/agershun/alasql/blob/develop/test/test306.js), [test307.js](https://github.com/agershun/alasql/blob/develop/test/test307.js), [test308.js](https://github.com/agershun/alasql/blob/develop/test/test308.js), [test309.js](https://github.com/agershun/alasql/blob/develop/test/test309.js), [test310.js](https://github.com/agershun/alasql/blob/develop/test/test310.js), [test311.js](https://github.com/agershun/alasql/blob/develop/test/test311.js), [test312.js](https://github.com/agershun/alasql/blob/develop/test/test312.js), [test313.js](https://github.com/agershun/alasql/blob/develop/test/test313.js), [test314.js](https://github.com/agershun/alasql/blob/develop/test/test314.js), [test315.js](https://github.com/agershun/alasql/blob/develop/test/test315.js), [test318.js](https://github.com/agershun/alasql/blob/develop/test/test318.js), [test319.js](https://github.com/agershun/alasql/blob/develop/test/test319.js), [test320.js](https://github.com/agershun/alasql/blob/develop/test/test320.js), [test321.js](https://github.com/agershun/alasql/blob/develop/test/test321.js), [test322.js](https://github.com/agershun/alasql/blob/develop/test/test322.js), [test323.js](https://github.com/agershun/alasql/blob/develop/test/test323.js), [test328.js](https://github.com/agershun/alasql/blob/develop/test/test328.js), [test337.js](https://github.com/agershun/alasql/blob/develop/test/test337.js), [test343.js](https://github.com/agershun/alasql/blob/develop/test/test343.js), [test346.js](https://github.com/agershun/alasql/blob/develop/test/test346.js), [test385.js](https://github.com/agershun/alasql/blob/develop/test/test385.js), [test386.js](https://github.com/agershun/alasql/blob/develop/test/test386.js), [test406.js](https://github.com/agershun/alasql/blob/develop/test/test406.js), [test411.js](https://github.com/agershun/alasql/blob/develop/test/test411.js), and [test606.js](https://github.com/agershun/alasql/blob/develop/test/test606.js)

See also: [[RETURN]]