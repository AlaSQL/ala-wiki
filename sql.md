# AlaSQL SQL Statements

* [Single and multiple SQL statements](Multiple-Statements)
* [Standard](Standard-Interface) and [fluent (like LINQ)](Fluent-Interface) interface
* [Literals](Literals)
* [Case-sensitive keywords](Case-Sensitive)
* [Comments](Comments)
* [Data types](Data-types)

## Short list by category

Data query

* [SELECT](Select) - for relational data
* [SEARCH](Search) - for nested JSON objects

Expression statement
* [= Expression Statement](Expression-Statement)

Data manipulation

* [INSERT](Insert), [INSERT OR REPLACE](Insert Or-Replace), [REPLACE](Insert Or-Replace)
* [UPDATE](Update)
* [DELETE](Delete)

Data definition

* [CREATE TABLE](Create-Table)
* [ALTER TABLE](Alter-Table)
* [DROP TABLE](Drop-Table)
* [CREATE VIEW](Create-View)
* [DROP VIEW](Drop-View)

Database

* [USE DATABASE](Use-Database)
* [CREATE DATABASE](Create-Database)
* [DROP DATABASE](Drop-Database)

External database
* [ATTACH DATABASE](Attach-Database)
* [DETACH DATABASE](Detach-Database)

[Transactions](Transactions)
* [BEGIN TRANSACTION](Begin-Transaction)
* [COMMIT TRANSACTION](Commit-Transaction)
* [ROLLBACK TRANSACTION](Rollback)

Show

* [SHOW DATABASES](Show-Databases)
* [SHOW TABLES](Show-Tables)
* [SHOW CREATE TABLE](Show Create-Table)

Program
* [DECLARE](Declare)
* [SET](Set)
* [IF THEN](If Then-Else), [IF THEN ELSE](If Then-Else)
* [BEGIN END](Begin-End)
* [WHILE](While)
* [SOURCE](Source)

Debug
* [ASSERT](Assert)

Information
* [HELP](Help)

## Full list

* [ASSERT](Assert)
* [ATTACH](Attach)
* ALTER TABLE
 * [ALTER TABLE ADD COLUMN](Add-Column)
 * [ALTER TABLE MODIFY COLUMN](Modify-Column)
 * [ALTER TABLE DROP COLUMN](Drop-Column)
 * [ALTER TABLE RENAME TABLE](Rename-Table)
* [BEGIN TRANSACTION](Begin-Transaction)
* [COMMIT TRANSACTION](Commit-Transaction)
* CREATE
 * [CREATE DATABASE](Create-Database)
 * [CREATE TABLE](Create-Table)
  * Column Types
  	* JavaScript data types
  	  * String
  	  * Number
  	  * Boolean
  	  * Date and ISODate
          * Emun
  	* ANSI SQL types
  	* SQLite, Oracle, MySQL, SQL Server, Postgres data types mapping
  * Column constraints
    * [PRIMARY KEY](Primary-Key)
    * [FOREIGN KEY](Foreign-Key)
    * [DEFAULT](Default)
    * [NULL](Null) / [NOT NULL](Not-Null)
    * [AUTO_INCREMENT](Identity), [AUTOINCREMENT](Identity), [IDENTITY](Identity)
    * [CHECK](Check)
  * [CREATE TRIGGER](Create-Trigger)
  * [CREATE GRAPH](Create-Graph)
  * [CREATE EDGE](Create-Edge)
  * [CREATE VERTEX](Create-Vertex)
* [DELETE](Delete)
* DROP
 * [DROP DATABASE](Drop-Database)
 * [DROP TABLE](Drop-Table)
 * [DROP TRIGGER](Drop-Trigger)
* INSERT
 * [INSERT SELECT](Insert-Select)
 * [INSERT VALUES](Insert-Values)
 * [INSERT DEFAULT VALUES](Insert Default-Values) 
* [RENAME TABLE](Rename-Table)
* [ROLLBACK TRANSACTION](Rollback-Transaction)
* [SELECT](Select)
 * [TOP](Top)
 * [DISTINCT](Distinct)
 * [INTO](Into)
 * [FROM](From)
 * [JOIN](Join)
 * [GROUP BY](Group-By)
 * [HAVING](Having)
 * [ORDER BY](Order-By)
 * [LIMIT](Limit)
 * [OFFSET](Offset)
 * [UNION](Union)
 * [UNION ALL](Union-All)
 * [INTERSECT](Intersect)
 * [Minus](Except),[EXCEPT](Except)
* SHOW
 * [SHOW CREATE TABLE](Show Create-Table)
 * [SHOW COLUMNS](Show-Columns)
 * [SHOW DATABASES](Show-Databases)
 * [SHOW TABLES](Show-Tables)
* [UPDATE](Update)
* [USE DATABASE](Use-Database)

* [Operators](Operators)
 * Number
  * + - * / %
 * String 
  * +
 * [Comparing](Comparing)
  * = != < <= > >=
  * [BETWEEN](Between), [NOT BETWEEN](Not-Between)
 * [NULL](Null)
   * [IS NULL](Is-Null), [IS NOT NULL](Is Not-Null), [NOT NULL](Is Not-Null)
 * Inclusion
   * [IN](In), [NOT IN](Not-In), [CONTAINS](Contains)
* [SQL-Functions](Functions)
 * [ABS()](sql/abs.md)
 * [Custom functions](Custom-Functions)
* Complex Operators
  * [EXISTS](Exists), [NOT EXISTS](Not-Exists)
  * [IN](In), [NOT IN](Not-In)
  * [SOME](Some), [ANY](Any)
  * [ALL](All)
* [Aggregators](Aggregators)
 * [SUM()](Sum) 
 * [COUNT()](Count) 
 * [MIN()](Min) 
 * [MAX()](Max) 
 * [FIRST()](First)
 * [LAST()](Last) 
 * [MEDIAN()](Median) 
 * [AGGR()](Aggr)
 * [ARRAY()](Array)
 * [Statistical functions](Statistical-Functions)
 * [Custom aggregators](Custom-Aggregators)
* Grouping functions
 * [CUBE()](Cube)
 * [ROLLUP()](Rollup)
 * [GROUPING SETS()](Grouping-Sets)
* [Standard functions](Functions)
* [Subqueries / Sub SELECT operator](Subqueries)
* [User-defined SQL functions](User Defined-Functions)
* Type conversions
 * [CAST](Cast)
 * [CONVERT](Convert)
 * [FORMAT](Format)
 * [:: double-colon](Double-Colon)
