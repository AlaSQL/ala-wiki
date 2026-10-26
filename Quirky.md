# Quirky things about AlaSQL

### Column names

You can use

    [column] 

or 

    `column` 

for columns with spaces, special symbols, etc. This also applys to **column named with [reserved keywords](AlaSQL-Keywords)** independent of the letter case. So names like `date`, `begin`, `content`, `last`, `max`, `min`, `count`, `natural`, `path`, `right`, `show`, `temp`, `timeout`, `target`, `top`, `value`, and `work` needs to be wrapped.

### Escaping characters

alasql parses queries as JavaScript strings before parsing them as SQL. Because of this, you need to double escape special characters such as double quotes using two backslashes instead of one. For example:

    alasql('SELECT "You should \\"double escape\\" double quotes"')
