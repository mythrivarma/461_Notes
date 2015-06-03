# 461_Notes - Querying SQL Server #
**Current Status - Page No : 14**
##Chapter 1##
* Here is the logical query processing order of the six main query clauses:
 * FROM
 * WHERE
 * GROUP BY
 * HAVING
 * SELECT
 * ORDER BY

* Date Time Columns can be queried like this:
WHERE hiredate >= '20030101'
* ORDER BY clause is the first and only clause that is allowed to refer to column
aliases defined in the SELECT clause. That’s because the ORDER BY clause is the only one
to be evaluated after the SELECT clause
