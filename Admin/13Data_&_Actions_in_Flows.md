**What happends inside a flow stays inside a flow......**
.
.
.
.
.
.
.
Until you use a Data Element!
# What is a Data Element?
A data element in flow represents an action that the flow can take.
- Helps in getting record from database and put them in flow.
- Also let you create, delete, update & modify records.
- Always test in a sandbox first when using flow elements.

Flow is not connected to your data. Therefore to get the records in your org we use getRecord element.

# Communicate using the Action Element

The Action element can communicate with users, customers, and external systems. It can also perform some advanced automation tasks.
- Send an Email with an Email Alert
- Post to Chatter
- The Text Template, Your Communication Friend
- Submit a Record for Approval

# What Is a Global Variable?
Global variables exist in every flow. You don’t create them and you can’t change their values in the flow, but they give your flow access to very useful data that can be different each time the flow runs.

You can use global variables in fields that let you select a resource. Such fields usually contain placeholder text such as “Enter value or search resources…” or “Insert a resource…” 

In Flow Builder, global variables behave similarly to objects and fields: each global variable contains multiple values. To use a global variable in a flow, follow these steps.

1. While creating or editing an element, click in a field that lets you select a resource. Flow Builder displays the resources you can place in this field.
2. Under Global Variables, select a variable that starts with $. Flow Builder displays the fields available to the selected variable.
3. Select the field that holds the value that you want to use.

# Get the Running User’s Profile and Role Values
When creating flows, avoid hardcoding IDs. Hardcoding is when you manually enter a Salesforce ID into flows or code. An example of hardcoding in an Update Records element is setting criteria to check for “005i000006rZRFU”. Instead, you should retrieve the ID with a Get Records element, and check the ID that’s stored in the Get Records element’s record variable.

# Retrieve Custom Labels
If your organization’s users work in multiple languages, custom labels are very valuable. Custom labels contain a string of text that you can translate into multiple languages. After you define the translations, Salesforce displays custom labels to each user in the user’s native language. You can even use custom labels in flows.

In Flow Builder, use the $Label global variable (or, in some elements, the Custom Label global variable) to place a custom label anywhere that accepts a text resource, such as screen components, default values for fields, and text formulas. In this example, creating a task record, the value of the Subject field is set to the TaskPrintLabels global variable. Now when users view the task, its subject is in their own language.

# Other Important Global Variables
There are a few other global variables that can be useful when creating flows.

|**Global Variable**|**What It Does**|
|-------------------|----------------|
|**$Flow.CurrentDate** <br> (or Running Flow Interview > CurrentDate)|Retrieves the date that the element is run|
|**$Flow.CurrentDateTime** <br>(or Running Flow Interview > CurrentDateTime)|Retrieves the date/time that the element is run|
|**$Flow.InterviewStartTime**<br>(or Running Flow Interview > InterviewStartTime)|Retrieves the date/time that the flow first started running|
|**$Flow.FaultMessage**<br>(or Running Flow Interview > FaultMessage)|Retrieves the error message when a flow stops due to an error|
|**$Organization**<br>(or Running Org)|Retrieves information found on the Company Information page in Setup, such as your org’s name or address|
|**$Record**<br>(or Triggering [object name])|In a record-triggered flow, $Record retrieves data from the record that triggered the flow. (You used this global variable in a hands-on challenge to get the Company and ID of a newly created lead.)
You can also use $Record to:
- Update data on the record that triggered the flow.
- Update a group of records related to the triggering record.
|

# Retrieve Custom Metadata Values
Custom metadata isn’t a global variable, but it is a set of values that you can access globally: in Flow Builder and throughout your Salesforce org. For example, a custom metadata type can be used across flows, code, validation rules, and more.

In Flow Builder, you retrieve custom metadata in the same way you retrieve object records: using the Get Records element. When selecting the object, select the custom metadata type.

# Keep these quirks in mind when you work with subflows.

- The Subflow element can reference only Autolaunched flows and screen flows.
- In a screen flow, you can reference only another screen flow.
- If you reference an inactive flow, it runs only for users who have the Manage Flows permission.
- If a child flow has multiple versions, the parent flow runs the child flow’s active version. If a child flow has no active version, the parent flow runs the latest version.