# How Salesforce Organizes Your Data

You can access objects from the navigation bar. Select any record to drill into a specific account, contact, opportunity, or any other record in Salesforce.

# Some definitions
| **Terms** | **Definition**|
|------------------|------------------|
| **Record**| An item you're tracking in your database; if your data is like a spreadsheet, then a record is a row on the spreadsheet    |
| **Field** |A place where you store a value, like a name or address; using our spreadsheet example, a field would be a column on the spreadsheet   |
| **Object**| A table in the database; in that spreadsheet example, an object is a tab on the spreadsheet   |
| **Org**   | Short for “organization,” the place where all your data, configuration, and customization lives. You and your users log in to access it. You might also hear this called “your instance of Salesforce”   |
| **App**   | A set of fields, objects, permissions, and functionality to support a business process   |

# List of some Salesforce Standard Objects

* **Accounts** are the companies you’re doing business with.<br>
* You can also do business with individual people (like solo contractors) using something called **Person Accounts**.<br>
* **Contacts** are the people who work at an Account.<br>
* **Leads** are potential prospects. You haven’t yet qualified that they're ready to buy or what product they need. You don’t have to use Leads, but they can be helpful if you have team selling, or if you have different sales processes for prospects and qualified buyers. <br>
* **Opportunities** are qualified leads that you’ve converted.<br>
* **List views** allow you to see records that are important to you. Using filters, you and your sales reps can create customized lists of accounts, contacts, opportunities, or other records in Salesforce. <br>For example, a sales rep can create a list view of opportunities they own and add a filter on amount, to help them find their biggest deals in the pipeline.<br>
* Sales reps can use the **Opportunity Kanban**, a visualization tool for opportunities, to review deals organized by each stage in the pipeline. With drag-and-drop functionality, sales reps can move deals from one stage to another, and get personalized alerts on key deals in flight.<br>

# Reports and Dashboards

Similar to list views, reports are a list of records that meet the criteria you define. But unlike list views, with reports you can apply more complex filtering logic, summarize and group your data, perform calculations, and create more sophisticated visualizations of your data using dashboards.
* When you convert the Lead, you create an Account and Contact along with the Opportunity.