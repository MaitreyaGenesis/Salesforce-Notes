# What is Data Model?

- It’s a way to model what database tables look like in a way that makes sense to humans. 
- If you’re not familiar with databases, think about storing data in a spreadsheet. 
- For example, D’Angelo can use a spreadsheet to track all DreamHouse’s properties. Columns can store the address, cost, and other important attributes. Rows can store this information for each property that DreamHouse is selling. Database tables are set up in a similar way.

# Different Types of Objects

- standard objects, 
- custom objects, 
- external objects, 
- platform events, and 
- BigObjects

**Objects** are containers for your information, but they also give you special functionality. For example, when you create a custom object, the platform automatically builds things like the page layout for the user interface.<br>
Focus will be only on 2 type sof objects: **Standard and Custom**

    - **Standard objects** are objects that are included with Salesforce. <br>
    Common business objects like Account, Contact, Lead, and Opportunity are all standard objects.<br>

    - **Custom objects** are objects that you create to store information that’s specific to your company or industry. <br>
    For DreamHouse, D’Angelo wants to build a custom Property object that stores information about the homes his company is selling.

# Different Types of Fields

Every standard and custom object has fields attached to it. 
| **Field Type** | **Definition** | **Example**|
|------------------|------------------|------------------|
| **Identity**| A 15-character, case-sensitive field that’s automatically generated for every record. You can find a record’s ID in its URL.| An account ID looks like 0015000000Gv7qJ.|
| **System** |Read-only fields that provide information about a record from the system, like when the record was created or when it was last changed. |  CreatedDate, LastModifiedById, and LastModifiedDate.|
| **Name**| All records need names so you can distinguish between them. You can use text names or auto-numbered names that automatically increment every time you create a record. | A contact’s name can be Julie Bean. A support case’s name can be CA-1024.|
| **Custom**   | Fields you create on standard or custom objects are called custom fields.  | You can create a custom field on the Contact object to store your contacts’ birthdays.|