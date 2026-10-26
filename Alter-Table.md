# Keyword `ALTER TABLE`

Syntax:
```sql
    ALTER TABLE tableid ADD COLUMN columnid type;
    ALTER TABLE tableid RENAME COLUMN columnid TO newname;
    ALTER TABLE tableid DROP COLUMN columnid;
    ALTER TABLE tableid RENAME TO newname;
```

ADD COLUMN
```js
    alasql('ALTER TABLE City ADD COLUMN Continent STRING');
```
RENAME COLUMN
```js
    alasql('ALTER TABLE City RENAME COLUMN Continent TO WorldPart');
```
DROP COLUMN
```js
    alasql('ALTER TABLE City DROP COLUMN Continent');
```
RENAME TO
```ja
   alasql('ALTER TABLE City RENAME TO Capital');
```

See also: [ADD COLUMN](Add-Column), [RENAME TABLE](Rename-Table)