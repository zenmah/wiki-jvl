<!-- TITLE: Coding Standards -->
<!-- SUBTITLE: A quick summary of Coding Standards -->

# Naming Conventions

## T-SQL Naming Conventions

### General 

#### Do 

- Use **UpperCamelCase**  to specify the names of Sql objects, columns and variables in stored procedures 
-	Ensure the name is unique and does not exist as a reserved keyword such as **PARTITION**, **SELECT**, **TABLE**
-	Keep the length to a maximum of 30 characters
-	Names must begin with a letter and may not end with an underscore.
-	Only use letters, numbers and underscores in names.

#### Avoid

-	Descriptive prefixes or Hungarian notation such as `sp_` or `tbl`.
-	Plurals—use the more natural collective term where possible instead. For example
-	`staff` instead of `employees` or `people` instead of `individuals`.
-	Use of multiple consecutive underscores, these can be hard to read.
-	Abbreviations and if you have to use them make sure they are commonly understood.

### Tables

-	Use a collective name or, less ideally, a plural form. For example (in order of preference) `staff` and `employees`.
-	Avoid using prefixes like tbl_.
-	Avoid giving a table the same name as one of its columns and vice versa.
-	Avoid, where possible, concatenating two table names together to create the name of a relationship table. Rather than CarsMechanics prefer Services.

### Columns 

-	Always use the singular name, a column should always contain a single value.
-	Where possible avoid simply using `id` as the primary identifier for the table.
-	Do not add a column with the same name as its table and vice versa.
-	Always use lowercase except where it may make sense not to such as proper nouns.

### Aliasing

-	Should relate in some way to the object or expression they are aliasing. 
  -	Use shorthand notations when aliasing table names
-	 As a rule of thumb, the alias should be the first letter of each word in the object's name.
  -	If there is already an alias with the same name then append a number.
-	Always include the `AS` keyword—makes it easier to read as it is explicit.
-	 For computed data (`SUM()` or `AVG()`) use the name you would give it were it a column defined in the schema.


```sqlserver
SELECT FirstName AS fn
FROM Staff AS s1
  JOIN Students AS s2 ON s2.MentorCode = s1.StaffNum;
```

```sqlserver
SELECT SUM(s.MonitorTally) AS MonitorTotal
FROM staff AS s;
```

### Stored Procedure 
-	The name must contain a verb.
-	Do not prefix with `sp_` or any other such descriptive prefix.
-	When calling a stored procedure always include the parameter names. 

### Variables & Parameters
- When using variables and/or parameters 

## Dimensions
### Fields
Use the following naming conventions for the dimension fields
Transform ...ID Fields in source tables to a ...Code field in the DWH. For example: 

|Source Field Types |	DWH Name	| Translation [EN]	| Translation [NL] |
| --- | --- | --- | --- |
| …ID |…Code| - | - | 

SalesID
InvoiceID	
SalesCode
InvoiceCode	-
Sales Code
Invoice Code	-
Sales Code
Invoice Code

### Surrogate keys
Surrogate Keys in dimensions always end with ID.

### Enumeration dimensions 
For enumerations, a number value is stored in the source database, that needs to be translated to a corresponding description.
Dimensions based on enumerations should adhere to the following convention: the value should be called `...Code`, the corresponding description called `...Description`.

| Field | DWH Name |
| --- | --- |
| Value/OptionID |	…Code	|
|Description	|…Description	|
||…CodeDescription	|
