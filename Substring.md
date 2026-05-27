# Keyword `SUBSTRING`

AlaSQL supports ```SUBSTRING(string, start, length)``` function:

```string```: The string you want to slice.

```start```: Where the substring should start. Positive value counts from left. First character is ```1```. Zero and negative values count from right where ```0``` is the last character.

```length```: How many characters shall the substring have. If ```length``` is left out or larger than the rest of the ```string```, then ```SUBSTRING``` returns all remaining characters.

## Examples

```sql
    SELECT SUBSTRING('abcd',1)
    -- returns 'abcd'
    SELECT SUBSTRING('abcd',3)
    -- returns 'cd'
    SELECT SUBSTRING('abcd',1,2)
    -- returns 'ab'
    SELECT SUBSTRING('abcd',2,2)
    -- returns 'bc'
    SELECT SUBSTRING('abcd',2,4)
    -- returns 'bcd'
    SELECT SUBSTRING('abcd',0) 
    -- returns 'd'
    SELECT SUBSTRING('abcd',-1)
    -- returns 'cd'
    SELECT SUBSTRING('abcd',-5,3)
    -- returns 'abc'
```

