# Functions

1. Compile-time standard library
 * String functions
   * [SUBSTRING()](Substring), [MID()](Mid), [INSTR()](Instr), [TRIM()](Trim)
 * Number functions
 * Logical functions
 * Date-time functions
   * [CONVERT()](Convert)
 * Unique identified functions
   * [NEWID(), UUID() and GEN_RANDOM_UUID()](Uuid)
2. Run-time standard library
 * [ROWNUM()](ROWNUM) (or [ROW_NUMBER()](ROWNUM))
 * [COALESCE()](Coalesce)
3. [User-defined functions](User-defined-functions)
4. Into-functions
5. From-functions
6. [Aggregators](Aggregators)
7. [User-defined aggregators](User-defined-aggregators)

Samples:
```sql
    ABS(), IIF(), IFNULL(), INSTR(), LOWER(), 
    UPPER(), LCASE(), UCASE(), LEN(), LENGTH()
    YEAR(date), DAYOFWEEK(date)
```

### Compatibility function

* [OBJECT_ID()](Object_id)

