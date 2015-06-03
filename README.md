# 461_Notes - Querying SQL Server #
**Current Status - Page No : 43**
* Check the differences between CONVERT, CAST, PARSE. Also check the TRY_ versions of the same.
* Try to Answer Qs in Sql Query Form in Technet (in your T-sql Bookmarks)
* Revisit page 42 after completing Chapters 11 and 15
* 

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
* There are a number of supported forms of aliasing: <expression> AS <alias>
as in empid AS employeeid, <expression> <alias> as in empid employeeid, and <alias> =
<expression> as in employeeid = empid
* If a Table name starts with a numeric value(or has an embedded space, or is a reserved T-SQL
keyword), then delimiters ("" or []) should be used while querying it.
* Float and Real are the datatypes with Maximum Range of values in numbers. But they are not recommended when we need accurate values. Accuracy takes a hit while using these data types.
* Fixed types use the storage for the indicated size; for example, CHAR(30) uses storage for 30 characters, whether
you actually specify 30 characters or less. This means that updates will not require the row to physically expand, and therefore no data shifting is required. So for attributes that get updated frequently, where the update performance is a priority, you should consider fixed types. Note that when compression is used—specifically row compression—SQL Server stores fixed types like variable ones, but with less overhead.
* With character strings, there’s also the question of using regular character types (CHAR,VARCHAR) vs. Unicode types (NCHAR, NVARCHAR). The former use 1 byte of storage per character and support only one language (based on collation properties) besides English. The latter use 2 bytes of storage per character (unless compressed) and support multiple languages.
* You also want to make sure that when indicating a literal of a type, you use the correct form. For example, literals of regular character strings are delimited with single quotation marks, as in 'abc', whereas literals of Unicode character strings are delimited with a capital N and then single quotation marks, as in N'abc'.
* As for the difference between CAST, CONVERT, and PARSE, with CAST, you indicate the expression and the target type; with CONVERT, there’s a third argument representing the style for the conversion, which is supported for some conversions, like between character strings and date and time values. For example, CONVERT(DATE, '1/2/2012', 101) converts the literal character string to DATE using style 101 representing the United States standard. With PARSE, you can indicate the culture by using any culture supported by the Microsoft .NET Framework. For example, PARSE('1/2/2012' AS DATE USING 'en-US') parses the input literal as a DATE by using a United States English culture.
* When using expressions that involve operands of different types, SQL Server usually converts the one that has the lower data type precedence to the one with the higher. Consider the expression 1 + '1' as an example. One operand is INT and the other is VARCHARINT precedes VARCHAR; hence, SQL Server implicitly converts the VARCHAR value '1' to the INT value 1, and the
result of the expression is therefore 2 and not the string '11'.
* Nonsequential GUIDs: You can generate nonsequential global unique identifiers to be stored in an attribute of a UNIQUEIDENTIFIER type. You can use the T-SQL function NEWID to generate a new GUID.
* Sequential GUIDs: You can generate sequential GUIDs within the machine by using the T-SQL function NEWSEQUENTIALID.
* 





