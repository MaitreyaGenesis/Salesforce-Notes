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

# Object Realtionships

- Object relationships are a special field type that connects two objects together.
- Eg: The Account to Contact relationship(Standard Relationship).

There are two main types of object relationships: **lookup and master-detail**.

# Lookup Relationships

In our Account to Contact example above, the relationship between the two objects is a lookup relationship. A lookup relationship essentially links two objects together so that you can “look up” one object from the related items on another object.

Lookup relationships can be **one-to-one or one-to-many**.<br>
The **Account to Contact** relationship is **one-to-many** because a single account can have many related contacts. For our DreamHouse scenario, you could create a one-to-one relationship between the Property object and a Home Seller object.

# Master-Detail Relationships

While lookup relationships are fairly casual, **master-detail relationships** are a bit **tighter**. In this type of relationship, one object is the master and another is the detail. The master object controls certain behaviors of the detail object, like who can view the detail’s data.

**For example**, say the owner of a property wanted to take their home off the market. DreamHouse wouldn’t want to keep any offers made on that property. With a master-detail relationship between Property and Offer, you can delete the property and all its associated offers from your system.

# Hierarchical Relationships

Hierarchical relationships are a special type of lookup relationship. **The main difference between the two is that hierarchical relationships are only available on the User object. You can use them for things like creating management chains between users.**

## Difference between Lookup Relationship and Master Detail Relationship

| **Lookup Relatonship** | **Master Detail Relationship** | 
| ---------------- | ---------------- | 
| Lookup relationships are fairly casual.  | Master-detail relationships are a bit tighter.  | 
| A lookup relationship essentially links two objects together so that you can “look up” one object from the related items on another object.  |  In this type of relationship, one object is the master and another is the detail. The master object controls certain behaviors of the detail object, like who can view the detail’s data. | 
| Objects in lookup relationships usually work as stand-alone objects.  | In a master-detail relationship, the detail object doesn’t work as a stand-alone. It’s highly dependent on the master. | 
|Parent field is optional on child records. We can set it up required or not required. |Parent field (that is master) is always required field on child records. |
|Roll-up summary is not possible here. Needs extra customization to achieve this.|Roll-up summary is possible here.|
|Each child record has an owner & can be changed independently. It is not related to the parent record.|The owner field on the detail & sub-detail record is not available to change & is automatically set to the owner of the master detail.|
|Cross object workflow field update is not possible here.|Cross object workflow field update is possible here.|
|Maximum 40lookup relationships can be created on 1 child object.|Maximum 2 Master Detail Relationships can be created on 1 child object.|
|Standard objects can be parent or child.|Standard objects can't be on detail i.e. on child side. That is both standard objects & custom objects can be master objects. Only custom object can be on detail side.|
|Cascade delete is not possible directly. It needs customization to achieve it. We can configure options to either clear the parent field value in the child record or prevent the deletion of the parent record.|Cascade delete happends when master record gets deleted. That is when master record is deleted, all detail records get deleted automaticaly & when child records get deleted.|
|Re-parenting is not possible here. Needs extra handling to achieve this.|Re-parenting can be stopped so that parent record cannot be changed on child records.|
|On child object we can have sharing rules, manual sharing, queues, etc independently & has no dependency on parent.|Detail objects of a master-detail relationship cannot have sharing rules, manual sharing or queues as these require owner field.|
|To implement this relationship there are no limitations of existing or non-existing records in child object.| To implement this realtionship no records should exist in the child object. If a child record exists then first lookup relationship has to be created & then lookup parent has to be populated on child records. Then lookup will be converted into Master-Detail Relationship.|