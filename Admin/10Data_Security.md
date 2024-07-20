# Introduction
- Salesforce includes simple-to-configure security controls that make it easy to specify which users can *view, create, edit, or delete* any record or field in the app. 
- You can configure access at the level of the organization, objects, fields, or individual records. 
- By combining security controls at different levels, you can provide just the right level of data access to thousands of users without having to specify permissions for each user individually.
- This is basically controlling what your users can access in **User Management Part**.

# Levels of Data Access

You can configure access to data in Salesforce at four main levels.<br>

1. **Organization**<br>
At the highest level, you can secure access to your organization by maintaining a list of authorized *users, setting password policies, and limiting login access to certain hours and certain locations*.

2. **Objects**<br>
- Object-level security provides the simplest way to control which users have access to which data. By setting permissions on a particular type of object, you can prevent a group of users from creating, viewing, editing, or deleting any records of that object. 
- For example, you can use object permissions to ensure interviewers can view positions and job applications but not edit or delete them. 
**- We recommend you use permission sets and permission set groups to configure object permissions**.

3. **Fields**<br>
- Field-level security restricts access to certain fields, even for objects a user has access to. 
- For example, you can make the salary field in a position object invisible to interviewers but visible to hiring managers and recruiters. 
- Field permissions are also configured in permission sets.

4. **Records**<br>
- To control data with greater precision, you can allow particular users to view an object, but then restrict the individual object records they're allowed to see. 
- For example, record-level access allows interviewers to see and edit their own reviews, without exposing the reviews of other interviewers. 
- You set the default level of access that users have to each others’ records using organization-wide defaults. 
- Then, you can use the *role hierarchy, sharing rules, manual sharing, and other sharing features* to open up access to records.<br>

Let’s take a closer look at two features used to configure data access: *permission sets and organization-wide defaults*.

**Permission Sets**<br>
- Permission sets are collections of settings and permissions that determine what users can do in Salesforce. 
- Use permission sets to grant access to objects, fields, tabs, and other features and extend users’ access without changing their profiles.

*What’s so great about permission sets?* Because you can reuse smaller permission set building blocks, you can avoid creating dozens or even hundreds of profiles for each user and job function. That’s why we recommend you assign users the *Minimum Access - Salesforce profiles*, and then use permission sets and permission set groups to manage your users’ access.
*When you create permission sets, include all permissions necessary for a job or task*.

**Permission Set Groups - groups of permission sets**
- Use permission set groups to bundle permission sets together based on a job persona or role. 
- You can then assign a permission set group to users, rather than keep track of multiple permission set assignments. Users assigned a permission set group receive the combined permissions of all the permission sets in the group.
- What makes permission set groups so powerful is that you can include a permission set in more than one permission set group. 
- And you can mute specific permissions within a permission set group so the assigned users don’t have those permissions.
- When you put all these capabilities together, you can get efficient about your reuse of permission sets. 
- You can ensure your users have only the permissions they need for their jobs without needing to clone dozens (or hundreds!) of profiles to achieve the same setup.

**Organization-Wide Sharing Defaults**
- You can control data access with greater precision by allowing particular users to view an object, but then restricting the individual records within the object they’re allowed to see. 
- You use organization-wide defaults to specify the baseline level of access users have to records they don’t own.<br>

You can determine the organization-wide defaults by answering the following questions for each object.
![alt text](image-1.png)<br>
Based on your answers to these questions, you can set the sharing model for that object to one of the following settings.<br>

|**Field**|**Description**|
|**Private**|Only the record owner, and users above that role in the hierarchy, can view, edit, and report on those records.|
|**Public Read Only**|All users can view and report on records but not edit them. Only the owner, and users above that role in the hierarchy, can edit those records.|
|**Public Read/Write**|All users can view, edit, and report on all records.|
|**Controlled by Parent**|A user can perform an action (such as view, edit, or delete) on a record based on whether he or she can perform that same action on the record associated with it.|

- If you set the organization-wide sharing setting for an object as Private or Public Read Only, you can grant users more access to records by setting up a role hierarchy, defining sharing rules, or using other sharing features. 
- You can only use these features to grant more access—they can’t be used to restrict access to records beyond what was originally specified with the organization-wide sharing defaults.