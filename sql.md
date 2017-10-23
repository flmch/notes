# MySQL

## Topics

* add column based on other columns

```sql
alter table tbl
add column col1 float

update table tbl
set col1 = col2/col3
```

* rename column

```sql
rename table 'tbl1' to 'tbl2'
```

* group by year and month

```sql
select
	year(date)
	,month(date)
from tbl1
group by 
	year(date)
	,month(date)
```





# Sql Server

## Concepts

* Batch Separator GO
  GO is not a sql statement, it's a batch separator only understand by SSMS.
  Batch separator can not be used in stored procedure.

## Topics

### Stored Procedure

* create procedure if exist
  [sql server stored procedure tutorial](https://www.mssqltips.com/sqlservertutorial/160/sql-server-stored-procedure-tutorial/)
  [stackoverflow how to drop stored procedure](https://stackoverflow.com/questions/3386994/what-is-the-syntax-to-drop-a-stored-procedure-in-sql-server-2000)
```sql
-- drop stored procedure if exits
IF EXISTS (
    SELECT * FROM
    dbo.sysobjects
    WHERE id = OBJECT_ID(N'[db_name].[sp_name]')
    AND OBJECTPROPERTY(id, N'IsProcedure') =1 )
DROP PROCEDURE [db_name].[sp_name]
GO

-- create stored procedure
CREATE PROCEDURE sp_name
(
    @param1 varchar(200),
    @param2 varchar(200) OUTPUT
)
AS
BEGIN
    -- here is the main code
    SELECT @param2 = count(*)
    FROM [db].[table]
END
```

--------------------
* take table name as an input parameter
  [stackoverflow answer](https://stackoverflow.com/questions/22105121/how-to-take-table-name-as-an-input-parameter-to-the-stored-procedure)

``SET NOCOUNT ON`` is a set statement which prevents the message which shows the number of rows affected by T-SQL query statements. This is used within stored procedures and triggers to avoid showing the affected rows message. Using SET NOCOUNT ON within a stored procedure can improve the performance of the stored procedure by a significant margin.

```sql
ALTER PROCEDURE [dbo].[sp_tablenametest]
table_name varchar(50),
PMId int,
ValueEq int

AS
BEGIN
SET NOCOUNT ON;

DECLARE @cmd AS NVARCHAR(max)
SET @cmd = N'SELECT * FROM ' + @table_name + 
' WHERE Column1 = ''' + @PMId +  '''' +
' AND Column2= ''' + @ValueEq + ''''

EXEC sp_executesql @cmd 
END
```

### unclassified

* partition
```sql
OVER(PARTITION BY *** ORDER BY ***)

-- group
select
	row_number() over(partition by col1 order by col2) row_rank
from table

or

select 
	rank() over(partition by col1 order by col2) ranking
from table

--row_number() and rank() are called window functions
```
--------
* get table schema
```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE table_names = 'tablenames'
```
--------
* Loop in Sql Server
  There is no For loop in sql server, there is only WHILE loop, the syntax is:
```sql
DECLARE @a INT;
SET @a = 1;
WHILE @a < 10
BEGIN
	PRINT @a;
	SET @a = @a +1;
END;
```
--------
* WITH AS statment

------------
* temporary table; tempdb
  temporary table can be define with # or ## in front of table name.
  temporary tables are saved in tempdb, when use OBJECT_ID() function
  to retrieve temporary tables' id, database name must be explicitly specified.
  for example: IF OBJECT_ID('tempdb.dbo.#tblname', 'U') IS NOT NULL

-------------
* Exist Keyword

  SQL statements that use the EXISTS condition are very inefficient since the sub-query is RE-RUN for EVERY row in the outer query's table. 
  There are more efficient ways to write most queries, that do not use the EXISTS condition.

------------
* GROUP BY ... HAVING

------------
* delete table if exists
```sql
IF OBJECT_ID('[db_name].[table_name]', 'U') IS NOT NULL
DROP TALBE [db_name].[table_name]
```

----------
* concat column

```sql
select
	concat(col1, col2, col3 ...)
from table
```

## Useful Functions

row_number()
DATEDIFF()
convert(to_datatype, expression)
substring(str, startpos, len)



















