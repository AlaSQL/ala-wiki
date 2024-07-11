# DATE

AlaSQL supports two different date types:
* Date - JavaScript date type (object)
* DATE - SQL date type (string like 'YYYYMMDD')

See the example:
```js
    alasql('CREATE TABLE orders (orderdate Date)');
    alasql('INSERT INTO orders VALUES ("2014-01-01")');
    var res = alasql('SELECT * FROM orders');

    // It gives a JavaScript dates
    var res = alasql('SELECT orderdate->getUTCFullYear() FROM orders');

    // This is gives an array of years
    // Here - getUTCFullYear() - is a function of object Date.prototype
```

If you want to use good old SQL date just use `DATE`, instead `Date`:
```js
    alasql('CREATE TABLE sample (sqldate DATE, jsdate Date)');
```
See a [jsFiddle example](http://jsfiddle.net/b94d5e3w/)

Please note that Javascript will use locale when working with dates, so make sure always to ask for UTC time. Example: for the Date `2014-01-01` the `.getFullYear()` (missing `UTC`) will give you `2013` if you are located west of london. 

NOTE: When `alasql.options.dateAsString` (default: true) is set to false, JavaScript dates are  _always_ used. 
JavaScript dates are easier to work with then string dates, especially when the time component is of relevance in the data (for example when sorting or using `BETWEEN`).
The following date functions are affected by this configuration property: `NOW()`, `DATE()`, `GETDATE()`, `CURRENT_TIMESTAMP()`, `CURDATE()` and `CURRENTDATE()`.

## Relevant date functions

### DATE(dateString)
Returns a JavaScript date object based on the given date string.
`SELECT DATE("20081012")` or `SELECT DATE("2008.10.12")` or in ISO string format `SELECT DATE("1995-12-17T03:24:00")`.

### NOW(), GETDATE(), CURRENT_TIMESTAMP/CURRENT_TIMESTAMP()
Aliases for returning the current date (including time) as either a JavaScript Date object or a date string (with time component) (depending on `alasql.options.dateAsString`).

### CURDATE/CURDATE(), CURRENTDATE/CURRENTDATE()
Aliases for returning the current date (no time component). Depending on `alasql.options.dateAsString`, either a JavaScript Date object is returned or a date string (no time component).
In case a JavaScript date is returned, the time will be set to `00:00:00`.

### SECOND(date) / MINUTE(date), / HOUR(date) / DAY(date) / MONTH(date) / YEAR(date) / DAYOFWEEK(date)
Returns the number of <unit> for the given JavaScript date object.

### DATEDIFF(period, date1, date2)
Returns the difference between two given JS date objects, in the unit configured.
The units can be the following (and how these are interpreted by AlaSQL):

* `year` - 365 days
* `quarter`: 91.25 days
* `month`: 30 days
* `week`: 7 days
* `day`: 1 day
* `hour`: 1 hour
* `minute`: 1 minute
* `second`: 1 second
* `millisecond`: 1 millisecond
* `microsecond`: 0.001 millisecond

Example: `SELECT DATEDIFF(day, DATE("1995-12-17T03:24:00"), NOW())`

### DATEADD(unit, value, date)

Adds a given number of <unit> to the given date.

Example: `SELECT DATEADD(day, -2, NOW())` would subtract 2 days from today (including time).

### DATE_ADD(unit, valueInMs) / ADDDATE(unit, valueInMs)
Does the same as `DATEADD`, except that no unit can be passed. The value must be in milliseconds.

Example: `SELECT DATE_ADD(NOW(), 24 * 3600 * 1000)` would add one day to today.

### DATE_SUB(unit, valueInMs) / SUBDATE(unit, valueInMs)
Does the same as `DATE_ADD`, but subtracts instead of adds.

Example: `SELECT DATE_SUB(NOW(), 24 * 3600 * 1000)` would subtract one day from today.
