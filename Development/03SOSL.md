Salesforce Object Search Language (SOSL) is a Salesforce search language that is used to perform text searches in records. Use SOSL to search fields across multiple standard and custom object records in Salesforce. SOSL is similar to Apache Lucene.

Adding SOSL queries to Apex is simple—you can embed SOSL queries directly in your Apex code. When SOSL is embedded in Apex, it is referred to as **inline* SOSL**.<br>

```
List<List<SObject>> searchList = [FIND 'SFDC' IN ALL FIELDS 
                                      RETURNING Account(Name), Contact(FirstName,LastName)];
```

**Differences and Similarities Between SOQL and SOSL**<br>

Like SOQL, SOSL allows you to search your organization’s records for specific information. Unlike SOQL, which can only query one standard or custom object at a time, a single SOSL query can search all objects.

Another difference is that SOSL matches fields based on a word match while SOQL performs an exact match by default (when not using wildcards). For example, searching for 'Digital' in SOSL returns records whose field values are 'Digital' or 'The Digital Company', but SOQL returns only records with field values of 'Digital'.

SOQL and SOSL are two separate languages with different syntax. Each language has a distinct use case:

- Use SOQL to retrieve records for a single object.
- Use SOSL to search fields across multiple objects. SOSL queries can search most text fields on an object.

**Use the Query Editor**<br>

The Developer Console provides the Query Editor console, which enables you to run SOSL queries and view results. The Query Editor provides a quick way to inspect the database. It is a good way to test your SOSL queries before adding them to your Apex code. When you use the Query Editor, you need to supply only the SOSL statement without the Apex code that surrounds it.<br>
```FIND {Wingo} IN ALL FIELDS RETURNING Account(Name), Contact(FirstName,LastName,Department)```
<br>

# Basic SOSL Syntax
SOSL allows you to specify the following search criteria:
- Text expression (single word or a phrase) to search for
- Scope of fields to search
- List of objects and fields to retrieve
- Conditions for selecting rows in the source objects
This is the syntax of a basic SOSL query in Apex: 

```FIND 'SearchQuery' [IN SearchGroup] [RETURNING ObjectsAndFields]```
<br>
Remember that in the Query Editor and API, the syntax is slightly different:

```FIND {SearchQuery} [IN SearchGroup] [RETURNING ObjectsAndFields]```
<br>

*SearchQuery* is the text to search for (a single word or a phrase). Search terms can be grouped with logical operators (AND, OR) and parentheses. Also, search terms can include wildcard characters (*, ?). The * wildcard matches zero or more characters at the middle or end of the search term. The ? wildcard matches only one character at the middle or end of the search term.<br>
*SearchGroup* is optional. It is the scope of the fields to search. If not specified, the default search scope is all fields. SearchGroup can take one of the following values.

- `ALL FIELDS`
- `NAME FIELDS`
- `EMAIL FIELDS`
- `PHONE FIELDS`
- `SIDEBAR FIELDS`
*ObjectsAndFields* is optional. It is the information to return in the search result—a list of one or more sObjects and, within each sObject, list of one or more fields, with optional values to filter against. If not specified, the search results contain the IDs of all objects found.<br>
S**ingle Words and Phrases**<br>

A SearchQuery contains two types of text:

- **Single Word**— single word, such as test or hello. Words in the SearchQuery are delimited by spaces, punctuation, and changes from letters to digits (and vice-versa). Words are always case insensitive.
- **Phrase**— collection of words and spaces surrounded by double quotes such as "john smith". Multiple words can be combined together with logic and grouping operators to form a more complex query.