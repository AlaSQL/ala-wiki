# SQL Compabillity

See list of [[Supported SQL statements]]

See also the full list of [AlaSQL reserved keywords](AlaSQL keywords).

The list of keywords used in AlaSQL (based on the table from [here](https://web.archive.org/web/20170427161717/http://developer.mimer.com/standard/reservedwords/sql-reserved-words.tml)).

Keyword | SQL-92 | SQL-99 | SQL-2003 | SQL-2008 | SQL-2011 | AlaSQL
--- | --- | --- | --- | --- | --- | ----
[ABS](Abs) |   |   |   | √ | √ |  √
ABSOLUTE | √ | √ |   |   |   |  
ACTION | √ | √ |   |   |   |  
ADD | √ | √ |   |   |   | √
AFTER |   | √ |   |   |   | √
ALL | √ | √ | √ | √ | √ | √
ALLOCATE | √ | √ | √ | √ | √ | 
ALTER | √ | √ | √ | √ | √ | √
[AND](And) | √ | √ | √ | √ | √ | √
[ANY](Any) | √ | √ | √ | √ | √ | √
ARE | √ | √ | √ | √ | √ |  
ARRAY |   | √ | √ | √ | √ |  
ARRAY_AGG |   |   |   | √ | √ |  
ARRAY_MAX_CARDINALITY |   |   |   |   | √ |  
AS | √ | √ | √ | √ | √ | √
[ASC](Asc) | √ | √ |   |   |   |  √
ASENSITIVE |   | √ | √ | √ | √ |  
ASSERTION | √ |   |   |   |   |  
ASYMMETRIC |   | √ | √ | √ | √ | 
AT | √ | √ | √ | √ | √ | √
ATOMIC |   | √ | √ | √ | √ | 
AUTHORIZATION | √ | √ | √ | √ | √ | 
[AVG](Avg) | √ |   |   | √ | √ | √ 
BEFORE |   | √ |   |   |   |  
[BEGIN](Begin) | √ | √ | √ | √ | √ | √
BEGIN_FRAME |   |   |   |   | √ |  
BEGIN_PARTITION |   |   |   |   | √ |  
BETWEEN | √ | √ | √ | √ | √ | √
BIGINT |   |   | √ | √ | √ |  
BINARY |   | √ | √ | √ | √ |  
BIT | √ | √ |   |   |   |  
BIT_LENGTH | √ |   |   |   |   |  
BLOB |   | √ | √ | √ | √ |  
BOOLEAN |   | √ | √ | √ | √ |  
BOTH | √ | √ | √ | √ | √ | 
BREADTH |   | √ |   |   |   |  
BY | √ | √ | √ | √ | √ | √
CALL | √ | √ | √ | √ | √ | 
CALLED |   |   | √ | √ | √ | 
CARDINALITY |   |   |   | √ | √ |  
CASCADE | √ | √ | √ | √ | √ |  
CASCADED | √ | √ | √ | √ | √ |  
[CASE](Case) | √ | √ | √ | √ | √ | √
[CAST](Cast) | √ | √ | √ | √ | √ | √
CATALOG | √ | √ |   |   |   |  
CEIL |   |   |   | √ | √ |  
CEILING |   |   |   | √ | √ |  
CHAR | √ | √ | √ | √ | √ |  
CHAR_LENGTH | √ |   |   | √ | √ |  
CHARACTER | √ | √ | √ | √ | √ |  
CHARACTER_LENGTH | √ |   |   | √ | √ |  
[CHECK](Check) | √ | √ | √ | √ | √ | √
CLOB |   | √ | √ | √ | √ |  
CLOSE | √ | √ | √ | √ | √ | √
COALESCE | √ |   |   | √ | √ |  √
COLLATE | √ | √ | √ | √ | √ | 
COLLATION | √ | √ |   |   |   |  
COLLECT |   |   |   | √ | √ |  
COLUMN | √ | √ | √ | √ | √ | √
COMMIT | √ | √ | √ | √ | √ | √
CONDITION | √ | √ | √ | √ | √ | 
CONNECT | √ | √ | √ | √ | √ | 
CONNECTION | √ | √ |   |   |   |  
[CONSTRAINT](Constraint) | √ | √ | √ | √ | √ | √
CONSTRAINTS | √ | √ |   |   |   | √
CONSTRUCTOR |   | √ |   |   |   |  
[CONTAINS](Contains) | √ |   |   |   |   |  
CONTINUE | √ | √ |   |   |   |  
CONVERT | √ |   |   | √ | √ |  
CORR |   |   |   | √ | √ |  
[CORRESPONDING](Corresponding) | √ | √ | √ | √ | √ | √
[COUNT](Count) | √ |   |   | √ | √ |  
COVAR_POP |   |   |   | √ | √ |  
COVAR_SAMP |   |   |   | √ | √ |  
CREATE | √ | √ | √ | √ | √ | √
[CROSS](Cross) | √ | √ | √ | √ | √ | √
[CUBE](Cube) |   | √ | √ | √ | √ |  √
CUME_DIST |   |   |   | √ | √ |  
CURRENT | √ | √ | √ | √ | √ | 
CURRENT_CATALOG |   |   |   | √ | √ |  
CURRENT_DATE | √ | √ | √ | √ | √ | 
CURRENT_DEFAULT _TRANSFORM_GROUP |   | √ | √ | √ | √ |  
CURRENT_PATH | √ | √ | √ | √ | √ | 
CURRENT_ROLE |   | √ | √ | √ | √ |  
CURRENT_ROW |   |   |   |   | √ |  
CURRENT_SCHEMA |   |   |   | √ | √ |  
[CURRENT_TIME](Current_Time) | √ | √ | √ | √ | √ | 
CURRENT_TIMESTAMP | √ | √ | √ | √ | √ | √
CURRENT_TRANSFORM _GROUP_FOR_TYPE |   | √ | √ | √ | √ |  
CURRENT_USER | √ | √ | √ | √ | √ | 
CURSOR | √ | √ | √ | √ | √ | 
CYCLE |   | √ | √ | √ | √ |  
DATA |   | √ |   |   |   |  
[DATE](Date) | √ | √ | √ | √ | √ | √ 
[DAY](Day) | √ | √ | √ | √ | √ | √
DEALLOCATE | √ | √ | √ | √ | √ | 
DEC | √ | √ | √ | √ | √ |  
DECIMAL | √ | √ | √ | √ | √ |  
[DECLARE](Declare) | √ | √ | √ | √ | √ | √
[DEFAULT](Default) | √ | √ | √ | √ | √ | √
DEFERRABLE | √ | √ |   |   |   |  
DEFERRED | √ | √ |   |   |   |  
[DELETE](Delete) | √ | √ | √ | √ | √ | √
DENSE_RANK |   |   |   | √ | √ |  
DEPTH |   | √ |   |   |   |  
DEREF |   | √ | √ | √ | √ |  
[DESC](Desc) | √ | √ |   |   |   |  √
DESCRIBE | √ | √ | √ | √ | √ | 
DESCRIPTOR | √ | √ |   |   |   |  
DETERMINISTIC | √ | √ | √ | √ | √ | 
DIAGNOSTICS | √ | √ |   |   |   |  
DISCONNECT | √ | √ | √ | √ | √ | 
[DISTINCT](Distinct) | √ | √ | √ | √ | √ | √
DO | √ | √ | √ | √ | √ | 
DOMAIN | √ | √ |   |   |   |  
[DOUBLE](Double Precision) | √ | √ | √ | √ | √ | √
[DROP](Drop) | √ | √ | √ | √ | √ | √
DYNAMIC |   | √ | √ | √ | √ |  
EACH |   | √ | √ | √ | √ |  
ELEMENT |   |   | √ | √ | √ |  
[ELSE](Else) | √ | √ | √ | √ | √ | √
ELSEIF | √ | √ | √ | √ | √ | 
[END](End) | √ | √ | √ | √ | √ | √
END_FRAME |   |   |   |   | √ |  
END_PARTITION |   |   |   |   | √ |  
END_EXEC |   |   |   | √ | √ |  
EQUALS |   | √ |   |   |   |  
ESCAPE | √ | √ | √ | √ | √ | √
EVERY |   |   |   | √ | √ |  
[EXCEPT](Except) | √ | √ | √ | √ | √ | √
EXCEPTION | √ | √ |   |   |   |  
EXEC | √ | √ | √ | √ | √ |  
EXECUTE | √ | √ | √ | √ | √ | √
[EXISTS](Exists) | √ | √ | √ | √ | √ | √
EXIT | √ | √ | √ |   |   |  
EXTERNAL | √ | √ | √ | √ | √ | 
EXTRACT | √ |   |   | √ | √ |  
[FALSE](False) | √ | √ | √ | √ | √ | √
FETCH | √ | √ | √ | √ | √ | 
FILTER |   | √ | √ | √ | √ |  
[FIRST](First) | √ | √ |   |   |   | √
FIRST_VALUE |   |   |   |   | √ |  
FLOAT | √ | √ | √ | √ | √ |  
FOR | √ | √ | √ | √ | √ | 
[FOREIGN](Foreign Key) | √ | √ | √ | √ | √ | √
FOUND | √ | √ |   |   |   |  
FRAME_ROW |   |   |   |   | √ |  
FREE |   | √ | √ | √ | √ |  
[FROM](From) | √ | √ | √ | √ | √ | √
FULL | √ | √ | √ | √ | √ | √
FUNCTION | √ | √ | √ | √ | √ | 
FUSION | √ | √ | √ |   |   |  
GENERAL |   | √ |   |   |   |  
GET | √ | √ | √ | √ | √ | √
GLOBAL | √ | √ | √ | √ | √ | √
[GO](Go) | √ | √ |   |   |   |  
GOTO | √ | √ |   |   |   |  
GRANT | √ | √ | √ | √ | √ | 
[GROUP](Group) | √ | √ | √ | √ | √ | √
[GROUPING](Grouping Sets) |   | √ | √ | √ | √ | √
GROUPS |   |   |   |   | √ |  
HANDLER | √ | √ | √ | √ | √ | 
[HAVING](Having) | √ | √ | √ | √ | √ | √
HOLD |   | √ | √ | √ | √ | 
[HOUR](Hour) | √ | √ | √ | √ | √ | √
[IDENTITY](Identity) | √ | √ | √ | √ | √ | √
[IF](If) | √ | √ | √ | √ | √ | √
IMMEDIATE | √ | √ | √ |   |   |  
[IN](In) | √ | √ | √ | √ | √ | √
INDICATOR | √ | √ | √ | √ | √ | 
INITIALLY | √ | √ |   |   |   |  
[INNER](Inner) | √ | √ | √ | √ | √ | √
INOUT | √ | √ | √ | √ | √ | 
INPUT | √ | √ | √ |   |   |  
INSENSITIVE | √ | √ | √ | √ | √ |  
[INSERT](Insert) | √ | √ | √ | √ | √ | √
INT | √ | √ | √ | √ | √ |  
INTEGER | √ | √ | √ | √ | √ |  
[INTERSECT](Intersect) | √ | √ | √ | √ | √ | √
INTERSECTION |   |   |   | √ | √ |  
INTERVAL | √ | √ | √ | √ | √ | 
[INTO](Into) | √ | √ | √ | √ | √ | √
IS | √ | √ | √ | √ | √ | √
ISOLATION | √ | √ |   |   |   |  
ITERATE |   | √ | √ | √ | √ | 
[JOIN](Join) | √ | √ | √ | √ | √ | √
KEY | √ | √ |   |   |   |  
LANGUAGE | √ | √ | √ | √ | √ | 
LARGE |   | √ | √ | √ | √ | 
[LAST](Last) | √ | √ |   |   |   |  
LAST_VALUE |   |   |   |   | √ |  
LATERAL |   | √ | √ | √ | √ |  
LEAD |   |   |   |   | √ |  
LEADING | √ | √ | √ | √ | √ | 
LEAVE | √ | √ | √ | √ | √ | 
[LEFT](Left) | √ | √ | √ | √ | √ | √
LEVEL | √ | √ |   |   |   |  
[LIKE](Like) | √ | √ | √ | √ | √ | √
LIKE_REGEX |   |   |   | √ | √ |  
LIMIT |   | √ |   |   |   |  
LN |   |   |   | √ | √ |  
LOCAL | √ | √ | √ | √ | √ | 
LOCALTIME |   | √ | √ | √ | √ | 
LOCALTIMESTAMP |   | √ | √ | √ | √ | 
LOCATOR |   | √ |   |   |   |  
LOOP | √ | √ | √ | √ | √ | 
[LOWER](Lower) | √ |   |   | √ | √ |  
MAP |   | √ |   |   |   |  
MATCH | √ | √ | √ | √ | √ | 
[MAX](Max) | √ |   |   | √ | √ | √ 
MEMBER |   |   | √ | √ | √ | 
MERGE |   |   | √ | √ | √ |  
METHOD |   | √ | √ | √ | √ | 
[MIN](Min) | √ |   |   | √ | √ | √ 
MINUTE | √ | √ | √ | √ | √ | √
MOD |   |   |   | √ | √ |  
MODIFIES |   | √ | √ | √ | √ | 
MODULE | √ | √ | √ | √ | √ | 
MONTH | √ | √ | √ | √ | √ | √
MULTISET |   |   | √ | √ | √ |  
NAMES | √ | √ |   |   |   |  
NATIONAL | √ | √ | √ | √ | √ | 
[NATURAL](Natural) | √ | √ | √ | √ | √ | √
NCHAR | √ | √ | √ | √ | √ |  
NCLOB |   | √ | √ | √ | √ |  
[NEW](New) |   | √ | √ | √ | √ | √
NEXT | √ | √ |   |   |   | 
NO | √ | √ | √ | √ | √ | 
NONE |   | √ | √ | √ | √ |  
NORMALIZE |   |   |   | √ | √ |  
[NOT](Not) | √ | √ | √ | √ | √ | √
NTH_VALUE |   |   |   |   | √ |  
NTILE |   |   |   |   | √ |  
[NULL](Null) | √ | √ | √ | √ | √ | √
[NULLIF](Null) | √ |   |   | √ | √ |  √
NUMERIC | √ | √ | √ | √ | √ |  
OBJECT |   | √ |   |   |   |  
OCTET_LENGTH | √ |   |   | √ | √ |  
OF | √ | √ | √ | √ | √ | √
[OFFSET](Offset) |   |   |   |   | √ | √
OLD |   | √ | √ | √ | √ | 
ON | √ | √ | √ | √ | √ | √
ONLY | √ | √ | √ | √ | √ |  
OPEN | √ | √ | √ | √ | √ | 
OPTION | √ | √ |   |   |   |  
[OR](Or) | √ | √ | √ | √ | √ | √
[ORDER](Order By) | √ | √ | √ | √ | √ | √
ORDINALITY |   | √ |   |   |   |  
OUT | √ | √ | √ | √ | √ | √
[OUTER](Outer) | √ | √ | √ | √ | √ |  √
OUTPUT | √ | √ | √ |   |   |  
OVER |   | √ | √ |   |   |  
OVERLAPS | √ | √ | √ | √ | √ | 
OVERLAY |   |   |   | √ | √ |  
PAD | √ | √ |   |   |   |  
PARAMETER | √ | √ | √ | √ | √ | 
PARTIAL | √ | √ |   |   |   |  
PARTITION |   | √ | √ | √ | √ |  
PATH | √ | √ |   |   |   |  
PERCENT |   |   |   |   | √ | √ 
PERCENT_RANK |   |   |   | √ | √ |  
PERCENTILE_CONT |   |   |   | √ | √ |  
PERCENTILE_DISC |   |   |   | √ | √ |  
PERIOD |   |   |   |   | √ |  
PORTION |   |   |   |   | √ |  
POSITION | √ |   |   | √ | √ |  
POSITION_REGEX |   |   |   | √ | √ |  
POWER |   |   |   | √ | √ |  
PRECEDES |   |   |   |   | √ |  
PRECISION | √ | √ | √ | √ | √ | √
PREPARE | √ | √ | √ | √ | √ | 
PRESERVE | √ | √ |   |   |   |  
[PRIMARY](Primary Key) | √ | √ | √ | √ | √ | √
PRIOR | √ | √ |   |   |   |  
PRIVILEGES | √ | √ |   |   |   |  
PROCEDURE | √ | √ | √ | √ | √ | 
PUBLIC | √ | √ |   |   |   |  
[RANGE](Range) | √ |   | √ | √ | √ | √ 
RANK |   |   |   | √ | √ |  
READ | √ | √ |   |   |   |  
READS |   | √ | √ | √ | √ | 
REAL | √ | √ | √ | √ | √ |  
RECURSIVE |   | √ | √ | √ | √ |  
REF |   | √ | √ | √ | √ |  
[REFERENCES](References) | √ | √ | √ | √ | √ | √
REFERENCING |   | √ | √ | √ | √ | 
REGR_AVGX |   |   |   | √ | √ |  
REGR_AVGY |   |   |   | √ | √ |  
REGR_COUNT |   |   |   | √ | √ |  
REGR_INTERCEPT |   |   |   | √ | √ |  
REGR_R2 |   |   |   | √ | √ |  
REGR_SLOPE |   |   |   | √ | √ |  
REGR_SXX |   |   |   | √ | √ |  
REGR_SXYREGR_SYY |   |   |   | √ | √ |  
RELATIVE | √ | √ |   |   |   |  
RELEASE |   | √ | √ | √ | √ | 
REPEAT | √ | √ | √ | √ | √ | 
RESIGNAL | √ | √ | √ | √ | √ | 
RESTRICT | √ | √ |   |   |   |  
RESULT |   | √ | √ | √ | √ | 
RETURN | √ | √ | √ | √ | √ | √
RETURNS | √ | √ | √ | √ | √ | √
REVOKE | √ | √ | √ | √ | √ | 
[RIGHT](Right) | √ | √ | √ | √ | √ | √
ROLE |   | √ |   |   |   |  
ROLLBACK | √ | √ | √ | √ | √ | √
[ROLLUP](Rollup) |   | √ | √ | √ | √ |  √
ROUTINE | √ | √ |   |   |   |  
ROW |   | √ | √ | √ | √ | √
ROW_NUMBER |   |   |   | √ | √ |  
ROWS | √ | √ | √ | √ | √ | 
SAVEPOINT |   | √ | √ | √ | √ |  
SCHEMA | √ | √ |   |   |   | √ 
SCOPE |   | √ | √ | √ | √ |  
SCROLL | √ | √ | √ | √ | √ | 
SEARCH |   | √ | √ | √ | √ | √ 
SECOND | √ | √ | √ | √ | √ | √
SECTION | √ | √ |   |   |   |  
SELECT | √ | √ | √ | √ | √ | √
SENSITIVE |   | √ | √ | √ | √ |  
SESSION | √ | √ |   |   |   |  
SESSION_USER | √ | √ | √ | √ | √ | 
[SET](Set) | √ | √ | √ | √ | √ | √
[SETS](Grouping Sets) |   | √ |   |   |   |  √
SIGNAL |   | √ | √ | √ | √ | 
SIMILAR |   | √ | √ | √ | √ |  
SIZE | √ | √ |   |   |   |  
SMALLINT | √ | √ | √ | √ | √ |  
[SOME](Some) | √ | √ | √ | √ | √ | √
SPACE | √ | √ |   |   |   |  
SPECIFIC | √ | √ | √ | √ | √ | 
SPECIFICTYPE |   | √ | √ | √ | √ |  
SQL | √ | √ | √ | √ | √ | 
SQLCODE | √ |   |   |   |   |  
SQLERROR | √ |   |   |   |   |  
SQLEXCEPTION | √ | √ | √ | √ | √ | 
SQLSTATE | √ | √ | √ | √ | √ | 
SQLWARNING | √ | √ | √ | √ | √ | 
SQRT |   |   |   | √ | √ |  
START |   | √ | √ | √ | √ | 
STATE |   | √ |   |   |   |  
STATIC |   | √ | √ | √ | √ | 
[STDDEV_POP]() |   |   |   | √ | √ |  
[STDDEV_SAMP]() |   |   |   | √ | √ |  
SUBMULTISET |   |   | √ | √ | √ |  
[SUBSTRING](Substring) | √ |   |   | √ | √ |  √
SUBSTRING_REGEX |   |   |   | √ | √ |  
SUCCEEDS |   |   |   |   | √ |  
[SUM](Sum) | √ |   |   | √ | √ |  √
SYMMETRIC |   | √ | √ | √ | √ | 
SYSTEM |   | √ | √ | √ | √ |  
SYSTEM_TIME |   |   |   |   | √ |  
SYSTEM_USER | √ | √ | √ | √ | √ | 
[TABLE](Create Table) | √ | √ | √ | √ | √ | √
TABLESAMPLE |   |   | √ | √ | √ |  
TEMPORARY | √ | √ |   |   |   | √
THEN | √ | √ | √ | √ | √ | √
TIME | √ | √ | √ | √ | √ | √
TIMESTAMP | √ | √ | √ | √ | √ | √
TIMEZONE_HOUR | √ | √ | √ | √ | √ | 
TIMEZONE_MINUTE | √ | √ | √ | √ | √ | 
TO | √ | √ | √ | √ | √ | √
TRAILING | √ | √ | √ | √ | √ | 
TRANSACTION | √ | √ |   |   |   |  
TRANSLATE | √ |   |   | √ | √ |  
TRANSLATE_REGEX |   |   |   | √ | √ |  
TRANSLATION | √ | √ | √ | √ | √ |  
TREAT |   | √ | √ | √ | √ |  
[[TRIGGER]] |   | √ | √ | √ | √ | √
TRIM | √ |   |   | √ | √ | √ 
TRIM_ARRAY |   |   |   |   | √ |  
[TRUE](True) | √ | √ | √ | √ | √ | √
TRUNCATE |   |   |   | √ | √ |  
UESCAPE |   |   |   | √ | √ |  
UNDER |   | √ |   |   |   |  
UNDO | √ | √ | √ | √ | √ |  
[UNION](Union) | √ | √ | √ | √ | √ | √
[UNIQUE](Unique) | √ | √ | √ | √ | √ | √
UNKNOWN | √ | √ | √ | √ | √ | 
UNNEST |   | √ | √ | √ | √ |  
UNTIL |   | √ | √ | √ | √ | 
[UPDATE](Update) | √ | √ | √ | √ | √ | √
[UPPER](Upper) | √ |   |   | √ | √ |  √
USAGE | √ | √ |   |   |   |  
USER | √ | √ | √ | √ | √ | 
[USING](Using) | √ | √ | √ | √ | √ | √
VALUE | √ | √ | √ | √ | √ | √
VALUES | √ | √ | √ | √ | √ | √
VALUE_OF |   |   |   |   | √ |  
VAR_POP |   |   |   | √ | √ | √
VAR_SAMP |   |   |   | √ | √ | √
VARBINARY |   |   |   | √ | √ |  
VARCHAR | √ | √ | √ | √ | √ | √
VARYING | √ | √ | √ | √ | √ | 
VERSIONING |   |   |   |   | √ |  
[VIEW](Create View) | √ | √ |   |   |   | √ 
WHEN | √ | √ | √ | √ | √ | √
WHENEVER | √ | √ | √ | √ | √ |  
WHERE | √ | √ | √ | √ | √ | √
[WHILE](While) | √ | √ | √ | √ | √ | √
WIDTH_BUCKET |   |   |   | √ | √ |  
WINDOW |   | √ | √ | √ | √ |  
[WITH](With) | √ | √ | √ | √ | √ | √
WITHIN |   | √ | √ | √ | √ |  
WITHOUT |   | √ | √ | √ | √ | 
WORK | √ | √ |   |   |   | √ 
WRITE | √ | √ |   |   |   |  
YEAR | √ | √ | √ | √ | √ | √
ZONE | √ | √ |   |   |   | 