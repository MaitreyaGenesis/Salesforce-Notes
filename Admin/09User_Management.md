# Who’s a user? 
- A user is anyone who logs in to Salesforce. 
- Users are employees at your company, such as sales reps, managers, and IT specialists, who need access to the company's records. 
- You can also have external users, such as end customers, prospects, and partners who access Experience Cloud sites.
- A user account exists for every user in Salesforce. 
- The user account identifies the user, and the user account settings determine what features and records the user can access. <br>
Each user account contains at least the following.

1. Username
Each user has both a username and an email address. The username must be formatted like an email address and must be unique across Salesforce. It can be the user’s email address, so long as it’s unique.
2. Email Address
3. User's First Name (optional)
4. User's Last Name
5. Alias
An alias is a short name to identify the user on list pages, reports, or other places where their entire name doesn't fit. By default, the alias is the first letter of the user's first name and the first four letters of their last name.
6. Nickname
7. License
A user license determines which features the user can access in Salesforce. For example, you can allow users access to standard Salesforce features and Chatter with the standard Salesforce license. But if you want to grant a user access to only some features in Salesforce, you have a host of licenses to choose from. For example, if you have to grant a user access to Chatter without allowing them to see any data in Salesforce, you can give them a Chatter Free license.

8. Profile
Each user has one profile that defines default settings. It’s possible to use profiles to grant permissions and access to users. However, we recommend you grant users the Minimum Access - Salesforce profile, and then use permission sets and permission set groups to grant users the permissions they require.
9. Role (optional)
Roles determine what users can see in Salesforce based on where they’re located in the role hierarchy. Users at the top of the hierarchy can see all the data owned by users below them. Users at lower levels can't see data owned by users above them, or in other branches, unless sharing rules grant them access. Roles are optional but each user can have only one. If you have an org with many users, you may find it easier to assign roles when adding users. However, you can set up a role hierarchy and assign roles to users at any time. Roles are only available in Professional, Enterprise, Unlimited, Performance, and Developer editions of Salesforce.

You view and manage users from the *Users page* in Setup. The user list shows all the users in Salesforce. From the list, you can:

1. Create one or more users.
2. Reset passwords for selected users.
3. View a user’s detail page by clicking the name, alias, or username.
4. Edit a user’s details.
5. Log in as any user if the system permission is enabled or if the user has granted you system administrator login access.

# What should be in a permission set vs. a profile?

|**Permission Set**|**Profile**|
|------------------|-----------|
|User, object, and field permissions|Default record types|
|Custom permissions|Default assigned apps|
|Connected app access|Page layout assignments|
|Apex class access|Login hours|
|Visualforce page access|Login IP ranges|
|Tab settings|   |

# Guidelines for adding users

- **Username**: Each user must have a username that is unique across all of Salesforce.
- **Username format**: Users must have a username in the format of an email address (jdoe@domain.com), but they don't have to use a real email address. They can use their email address if they wish as long as their email address is unique across all of Salesforce.
- **Email**: Users can have the same email address across organizations.
- **Passwords**: Users must change their password the first time they log in.
- **Login link**: Users can only use the login link in the sign-in email once. If a user follows the link and doesn’t set a password, you (the admin) must reset their password before they can log in.

# Freezing & Deactivating a User

- Both actions prevent the user from logging in to their account. 
- But freezing user accounts doesn’t make their user licenses available in your organization. 
- That’s why you’ll want to deactivate a user after they leave your company.
- You can deactivate users, but you can’t delete them. 
- **Why is this?** Deleting a user can result in orphaned records and the loss of critical business information. So to ensure the user’s records and data are preserved, you deactivate users instead.