To read a record from Salesforce, you must write a query. Salesforce provides the Salesforce Object Query Language, or SOQL in short, that you can use to read saved records. SOQL is similar to the standard SQL language but is customized for the Lightning Platform.

Because Apex has direct access to Salesforce records that are stored in the database, you can embed SOQL queries in your Apex code and get results in a straightforward fashion. When SOQL is embedded in Apex, it is referred to as inline SOQL.


To include SOQL queries within your Apex code, wrap the SOQL statement within square brackets and assign the return value to an array of sObjects. For example, the following retrieves all account records with two fields, Name and Phone, and returns an array of Account sObjects.

```Account[] accts = [SELECT Name,Phone FROM Account];```

**Use the Query Editor**<br>
The Developer Console provides the Query Editor console, which enables you to run your SOQL queries and view results. The Query Editor provides a quick way to inspect the database. It is a good way to test your SOQL queries before adding them to your Apex code. When you use the Query Editor, you must supply only the SOQL statement without the Apex code that surrounds it.<br>

```SELECT Name,Phone FROM Account```

# Basic SOQL Syntax
This is the syntax of a basic SOQL query:

```SELECT fields FROM ObjectName [WHERE Condition]```
The `WHERE` clause is optional. Let’s start with a very simple query. For example, the following query retrieves accounts and gets Name and Phone fields for each account.<br>
```SELECT Name,Phone FROM Account```
The query has `two` parts:

1. `SELECT Name,Phone`: This part lists the fields that you would like to retrieve. The fields are specified after the SELECT keyword in a comma-delimited list. Or you can specify only one field, in which case no comma is necessary (e.g. `SELECT Phone`).
2. `FROM Account`: This part specifies the standard or custom object that you want to retrieve. In this example, it’s `Account`. For a custom object called Invoice_Statement, it is Invoice_Statement__c.

**Filter Query Results with Conditions**<br

If you have more than one account in the org, they will all be returned. If you want to limit the accounts returned to accounts that fulfill a certain condition, you can add this condition inside the WHERE clause. The following example retrieves only the accounts whose names are SFDC Computing. Note that comparisons on strings are case-insensitive.

```SELECT Name,Phone FROM Account WHERE Name='SFDC Computing'``<br>
The `WHERE` clause can contain multiple conditions that are grouped by using logical operators (AND, OR) and parentheses. For example, this query returns all accounts whose name is SFDC Computing that have more than 25 employees:

```SELECT Name,Phone FROM Account WHERE (Name='SFDC Computing' AND NumberOfEmployees>25)```

**Order Query Results**<br>

When a query executes, it returns records from Salesforce in no particular order, so you can’t rely on the order of records in the returned array to be the same each time the query is run. You can however choose to sort the returned record set by adding an ORDER BY clause and specifying the field by which the record set should be sorted. This example sorts all retrieved accounts based on the Name field.

```SELECT Name,Phone FROM Account ORDER BY Name```<br>
The default sort order is in alphabetical order, specified as `ASC`. The previous statement is equivalent to:

```SELECT Name,Phone FROM Account ORDER BY Name ASC```<br>
To reverse the order, use the `DESC` keyword for descending order:

```SELECT Name,Phone FROM Account ORDER BY Name DESC```
You can sort on most fields, including numeric and text fields. You can’t sort on fields like rich text and multi-select picklists.<br>

**Limit the Number of Records Returned**<br>

You can limit the number of records returned to an arbitrary number by adding the `LIMIT n` clause where n is the number of records you want returned. Limiting the result set is handy when you don’t care which records are returned, but you just want to work with a subset of records. For example, this query retrieves the first account that is returned. Notice that the returned value is one account and not an array when using `LIMIT 1`.

```Account oneAccountOnly = [SELECT Name,Phone FROM Account LIMIT 1];```<br>

**Combine All Pieces Together**<br>
You can combine the optional clauses in one query, in the following order:
```
SELECT Name,Phone FROM Account
                   WHERE (Name = 'SFDC Computing' AND NumberOfEmployees>25)
                   ORDER BY Name
                   LIMIT 10
```
<br>

**Access Variables in SOQL Queries**<br>

SOQL statements in Apex can reference Apex code variables and expressions if they are preceded by a colon (:). The use of a local variable within a SOQL statement is called a **bind**.<br>
```
String targetDepartment = 'Wingo';
Contact[] techContacts = [SELECT FirstName,LastName
                          FROM Contact WHERE Department=:targetDepartment];
```
<br>
To get child records related to a parent record, add an inner query for the child records. <br>

```
SELECT Name, (SELECT LastName FROM Contacts) FROM Account WHERE Name = 'SFDC Computing'
```
<br>

**Query Record in Batches By Using SOQL For Loops**<br>


With a SOQL for loop, you can include a SOQL query within a for loop. The results of a SOQL query can be iterated over within the loop. SOQL for loops use a different method for retrieving records—records are retrieved using efficient chunking with calls to the query and queryMore methods of the SOAP API. By using SOQL for loops, you can avoid hitting the heap size limit.

SOQL for loops iterate over all of the sObject records returned by a SOQL query. The syntax of a SOQL forloop is either:<br>
```
for (variable : [soql_query]) {
    code_block
}
```
or
```
for (variable_list : [soql_query]) {
    code_block
}
```
Both  `variable` and  `variable_list` must be of the same type as the sObjects that are returned by the  `soql_query`.