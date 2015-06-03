# 461_Notes - Querying SQL Server #
**Current Status - Page No : 30**
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
* ORDER BY clause is the first and only clause (Top/Distinct?) that is allowed to refer to column
aliases defined in the SELECT clause. That’s because the ORDER BY clause is the only one
to be evaluated after the SELECT clause
* You cannot use ORDER BY on columns that have the text, ntext, image, or xml data types.
* One of most typical mistakes that T-SQL developers make is to assume that a query without an ORDER BY clause always returns the data in a certain order—for example, clustered index order. But if you understand that in set theory, a set has no particular order to its elements, you know that you shouldn’t make such assumptions. The only way in SQL to guarantee that the rows will be returned in a certain order is to add an ORDER BY clause. That’s just one of many examples for aspects of T-SQL that can be better understood if you understand the foundations of the language. Now, you know that why a view created with an order by clause, does not guarantee any order when we query it with out an order by clause.

##Chapter 2##

