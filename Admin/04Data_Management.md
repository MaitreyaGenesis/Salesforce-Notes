## Import Data

You can easily import external data into Salesforce. Supported data sources include any program that can save data in the comma delimited text format (.csv).

Salesforce offers two main methods for importing data.

**Data Import Wizard**—this tool, accessible through the Setup menu, lets you import data in common standard objects, such as contacts, leads, accounts, as well as data in custom objects. It can import up to 50,000 records at a time. It provides a simple interface to specify the configuration parameters, data sources, and the field mappings that map the field names in your import file with the field names in Salesforce.
**Data Loader**—this is a client application that can import up to 150 million records at a time, of any data type, either from files or a database connection. It can be operated either through the user interface or the command line. In the latter case, you need to specify data sources, field mappings, and other parameters via configuration files. This makes it possible to automate the import process, using API calls.

|**When to use Data Import Wizard**|**When to use Data Loader**|
|----------------------------------|---------------------------|
|You need to load less than 50,000 records.|You need to load 50,000 to 150 million records.|
|The objects you need to import are supported by the wizard.|You need to load into an object that is not supported by the Data Import Wizard.|
|You don’t need the import process to be automated.|You want to schedule regular data loads, such as nightly imports.|

# Salesforce Record ID

- A unique ID is given to all the records & users in Salesforce.
**Where can you find the record IDs?**
    - At the end of the URL.
    - From a report that contains ID fields.
    - Via API.
**Characteristics of Record IDs**
    - URL & Report return 15 digits ID.
    - API tools(Data Loader) return 18 digits ID.
    - Salesforce recoganizes both the 15 as well as 18 digit IDs.
Note: Excel does not differentiate between the 15 & 18 digit IDs.
Best Practice: use the 18 digit form.

**Record Owners**
    - All the records have a record owner. (owners are specified in import files.)
    - If the owner is not specified, the imported is the default owner.
    - If you use **Data Import Wizard**:<br>
        use name, ID, or for custom objects. External ID also works.
    - If you use **Data Loader**:<br>
        you must use Salesforce record ID.
- There are 2 types of Record IDs: **Parent ID** & **Child ID**.

**Parent Records**<br>
    - Child records are associated with Parent records in addition to an owner.
    - If the Parent Record is not specified, them the import will fail.
    - Data Loader uses Salesforce Record ID.

- Users & Accounts must be added before importing Opportunities.
- Once you get your Users in you can export theirs IDs & then match it with their User Names.
- Once you get your Accounts in you can export theirs IDs & then match it with their Account Names.
- VLookup is used for matching IDs.

# Clean & Prepare your data using Excel

This is a time consuming task but there are several tools that you can use to ease your task:
1. **Sort & Filter** 
- Find duplicates. Isolate data to standardized names, formats.
- Isolate certail groups of data:
    - To apply naming conventions
    - To locate blanks + identify incomplete records

2. **VLookup** 
- Match values between data sources that is matching Salesforce user IDs to the names of record owners.

3. **Paste Special...as Values** 
- Replace formulas with values.
- Cells can insert formulas.
- Formulas are dependent on the cells they reference.
- If you delete any cells that are used in the formula, you'll get an error.

4. **Format Cells** 
- Removing leading zeros.
- Lets you enter data that begins with zeros, such as zip codes & phone numbers.

5. **Find & Replace** 
- Enforce consistency. Remove unwanted spaces,symbols.
- Replace one value with another.

6. **Concatenate** 
- Combine separate fields into one.(area code & phone)

7. **Text to Columns** 
- Opposite of what concatenate does that is separate a single field into two.(first & last names)

8. **Save as .csv** 
- Convert Excel file into format for input.
- Saves excel files into a comma separated values format.
- Save as CSV:
    - convert all formulas to values
    - loses formatting
    - saves only the sheet being displayed

# Choosing the right tool

3 tools are available in the UI:
- Data Import Wizards(robust)
- Dataloader.io
- Data Loader

||**Data Import Wizard**|**Dataloader.io**|**Data Loader**|
|-|---------------------|-----------------|---------------|
|# of records|Upto 50k|upto 10k/month|50k+|
|Catches duplicates|yes(name, email)|yes (Record ID only)|
|Option to turn off Workflow|yes|no-must turn off Workflow in setup|
|Export Data|no|yes(contributes 10k/month)|yes|
|Import Opportunities, Cases, etc|no|yes|

# Things to Remember

Data Loader recoganizes 1 field for the address
    - Address 1 and Address 2 fields must be combined prior to import.
Data Loader matches on Record IDs only
    - It will not catch duplicate names or emails.
Workflow rules will fire on any records that meet the rules criteria
    - Deactivate workflow if you don't want it to execute.

# Best Practices for importing data

- Backup up your data!
    - Weekly export service
    - Export Using Data Loader
- Import a Test Batch First
    - Always do a test batch of 5 records.
    - Check each of these new records in Salesforce.
    - If successful, don't forget to *exculde* these records from your batch import file.
- Use Mass Delete to Undo a Bad Import
    -Allows deletion of upto 200 records at a time.
- Workflow & Validation
    -Remember to turn off any workflow that you don't want to fire as a result of any newly created records.
    -Validation Rules are in effect during a data import.
- Are you importing sensitive data?
    -Check your data visibility settings(roles, profiles, sharing rules).
    -Correctly setup ownership before import.

# Prepare your data for import

4 steps before import

1. Cleanup your data

**Why clean up your data?**

Accuracy
Usability
Credibility
Adoption

**What should you clean up?**

Remove duplicate records
Correct spelling and punctuation
Enforce naming conventions
Fill in incomplete records

2. Prepare Salesforce

    - Compare your data to each salesforce object.
    -Do you track data which are not created till now? If yes, then create custom fields.
    -Add picklist values.
    -Create External Lookup fields.

3. Prepare your import files

    -Match field names.
    -Add a column for record owner.
    -Add a column for Parent record.

4. Use automation to keep it clean
    - Use **Validation Rules** to prevent users from enetering values outside a certain range.
    - **Picklists** to limit choices and eliminate the risk of misspellings.
    - **Custom Lookup Fields** prevents users from creating duplicate records.
    - **Workflow Field Updates**  & **Formula Fields** can populate data automatically removing the potential manual error.
    -**Record Types** & **Page Layouts** ensure that the user see the fields in the picklist values they need.

# Data Export

You can easily export data from Salesforce, either **manually** or on an **automatic** schedule. The data is exported as a set of ***comma-separated values (CSV) files***. Data export tools provide a convenient way to obtain a copy of your Salesforce data, either for backup or for importing into a different system.

Salesforce offers **two** main methods for exporting data.

**Data Export Service**—an in-browser service, accessible through the Setup menu. It allows you to export data manually once every 7 days (for weekly export) or 29 days (for monthly export). You can also export data automatically at weekly or monthly intervals. Weekly exports are available in Enterprise, Performance, and Unlimited Editions. In Professional Edition and Developer Edition, you can generate backup files only every 29 days, or automatically at monthly intervals only.<br>
**Data Loader**—a client application that you must install separately. It can be operated either through the user interface or the command line. The latter option is useful if you want to automate the export process, or use APIs to integrate with another system.
Using the Data Export Service