# Literals

You can use these characters for databases, tables, and other objects names:
* A-Z
* a-z
* _ (underscore)
* 0-9 (except first character)

For example:
```sql
      CREATE TABLE students_a (
        _id serial NOT NULL,
        na_me nvarchar(50) NOT NULL,
        CONSTRAINT students_pkey PRIMARY KEY (_id)
      );
```
See the example [in jsFiddle](http://jsfiddle.net/4s36sb64/)

If you want to use other characters and spaces, please use square brackets ```[ ]``` or back-quote ``` ` ``` to enclose the name:
```sql
    SELECT [My column] FROM `Моя табличка-1234()` ORDER BY [今日]
```

See also: [Case sensivity in AlaSQL](Case-Sensitive)
