# Keyword `REQUIRE`

This command is using for loading AlaSQL plugins (standard or custom) or any other JavaScript files:

Syntax:
```sql
    REQUIRE std-plugin, "filename.js", ...
```

The list of [standard plugins](Standard-Plugins).

Example:
```sql
    REQUIRE ECHO;
    ECHO 1;
    REQUIRE "./myfn.js"; -- 
    SELECT myfn(a) FROM one;
```

See also: [SOURCE](Source)