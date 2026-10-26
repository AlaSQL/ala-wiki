# Keyword `USE DATABASE`

Syntax:
```sql
    USE [DATABASE] databaseid
```

```js
    alasql('CREATE DATABASE geo');
    alasql('USE geo');
```
To select current database:

```js
	alasql.use('test01');

	// or

	alasql('USE test01');    

	// or

	alasql('USE DATABASE test01');    
```

You can check current database name in alasql.useid property:

```js
    console.log('Current database:', alasql.useid);
```

See also: [CREATE DATABASE](Create-Database), [ATTACH DATABASE](Attach-Database)