# Creating a simple function in SQL Server

## Scalar User-defined Functions用户定义标量函数

### Calling Scalar UDFs
* The body of the function must be enclosed in a BEGIN/END block.
* Statements with side effects (insert/update/delete) and temporary tables may not be used. You can, however, use table variables. Table variables are allowed in UDFs because they are created as variables, not through DDL. DDL is viewed as producing a side effect and is not allowed.
* TRY/CATCH statements are not allowed since CATCH can have the side effect of masking the error state of a given function.
### Syntax
CREATE FUNCTION [schema_name.]function_name
<br>( [ @parameter [ AS ] [type_schema_name.] datatype 
<br>    [ = default ] [ READONLY ]
<br> , @parameter [ AS ] [type_schema_name.] datatype 
<br>    [ = default ] [ READONLY ] ]
)

RETURNS return_datatype

[ WITH { ENCRYPTION
<br>       | SCHEMABINDING
<br>       | RETURNS NULL ON NULL INPUT
<br>      | CALLED ON NULL INPUT
<br>      | EXECUTE AS Clause ]

[ AS ]

BEGIN

 [declaration_section]

 executable_section

 RETURN return_value

END;

#### Anotation
*schema_name*
<br>The name of the schema that owns the function.
<br>*function_name*
<br>The name to assign to this function in SQL Server.
<br>*@parameter*
<br>One or more parameters passed into the function.
<br>*type_schema_name*
<br>The schema that owns the data type, if applicable.
<br>*datatype*
<br>The data type for @parameter.
<br>*default*
<br>The default value to assign to @parameter.
<br>*READONLY*
<br>It means that @parameter can not be overwritten by the function.
<br>*return_datatype*
<br>The datatype of the function's return value.
<br>*ENCRYPTION*
<br>It means that the source for the function will not be stored as plain text in the system views in SQL Server.
<br>*SCHEMABINDING*
<br>It means that the underlying objects can not be modified so as to affect the function.
<br>*RETURNS NULL ON NULL INPUT*
<br>It means that the function will return NULL if any parameters are NULL without having to execute the function.
<br>*CALL ON NULL INPUT*
<br>It means that the function will execute the function even if any parameters are NULL.
<br>*EXECUTE AS clause*
<br>Sets the security context to execute the function.
<br>*return_value*
<br>The value returned by the function.
## Example
### Define a function
CREATE FUNCTION ReturnSite
( @site_id INT )

RETURNS VARCHAR(50)

AS

BEGIN

   DECLARE @site_name VARCHAR(50);

   IF @site_id < 10
      SET @site_name = 'TechOnTheNet.com';
   ELSE
      SET @site_name = 'CheckYourMath.com';

   RETURN @site_name;

END;
### Call a function
USE [test]
GO

SELECT dbo.ReturnSite(8);

GO
