# How to insert data into the table?

AlaSQL provides three different methods to insert data from array into table:
```js
    var data = [{a:1}, {a:2}];
    alasql('CREATE TABLE one');
    
    // Method 1
    alasql.tables.one.data = data;

    // Method 2
    alasql('SELECT * INTO one FROM ?',[data]);

    // Method 3
    alasql('INSERT INTO one SELECT * FROM ?',[data]);
```

If you download data from external file, you can use this syntax:
```js
    alaslq('CREATE table one; SELECT * INTO one FROM JSON("data.json")');
```