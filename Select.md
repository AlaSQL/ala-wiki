# SELECT

Select clauses:

* [WITH](With)
* [SELECT columns](Select Columns)
* [REMOVE COLUMNS](Remove Columns) columns / LIKE pattern
* [TOP](Top) / [LIMIT](Limit) [FETCH](Fetch)
* [DISTINCT](Distinct)
* [INTO](Into)
* [FROM](From)
* [JOIN](Join) [ON](On) / [USING](Using)
* [APPLY](Apply)
* [GROUP BY](Group By)
* [HAVING](Having)
* [WHERE](Where)
* [ORDER BY](Order By)
* [UNION](Union) / [UNION ALL](Union All) /[INTERSECT](Intersect) / [EXCEPT](Except)

[Return value modifiers](Modifiers)
* [VALUE](Value), [COLUMN](Column), [ROW](Row), [MATRIX](Matrix), [INDEX](Index), [TEXT](Text) …

[Columns](Select Columns)
```sql
    SELECT City.Name, City.*, Population AS p FROM Cities
```
[Operators](Operators)
```sql
    SELECT w*h+20 FROM ?
```

[Aggregators](Aggregators)
```sql
   SELECT SUM(x), COUNT(*) FROM arr
```
[Functions](Functions)
```sql
    SELECT LCASE(name), LEN(name) FROM names
```
