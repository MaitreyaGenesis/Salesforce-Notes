# Reports and Dashboards

Similar to list views, reports are a list of records that meet the criteria you define. But unlike list views, with reports you can apply more complex filtering logic, summarize and group your data, perform calculations, and create more sophisticated visualizations of your data using dashboards.
In its simplest form, a report is a list of records (like opportunities or accounts) that meet the criteria you define. But reports are much more than simple lists. To get the data you need, you can filter, group, and do math on records. You can even display them graphically in a chart!

# What Is a Report Type?
A report type is like a template. Choosing the right report type is important in building a report, because when you choose a report type, you’re selecting the records and fields that are available for your report. 

Each report type has a primary object and can optionally include related objects. Salesforce offers a variety of standard report types based on single objects, like Accounts, Leads, and Products, and with related objects, like Opportunities with Projects and Campaigns with Contacts. 

But sometimes a standard report type doesn’t provide all the objects and fields that you need. That’s where custom report types come in. For example, say that Erin Donaghue, sales rep at Ursa Major Solar, wants to report on all her leads that have associated activities. She could choose the Leads report type, but then her report would return all leads, not just those with activities. 

# What Is a Dashboard?
A dashboard is a visual display of key metrics and trends for records in your org. Each dashboard widget is based on a single source report. You can use the same or different source reports for the various widgets in a dashboard (for example, use the same report in a bar chart and pie chart). By adding multiple dashboard widgets to a single dashboard page, you can create a powerful visual display of data on a common theme, such as sales performance or customer support.

Like reports, dashboards are stored in folders. If you have access to a folder, you can view its dashboards. To view the individual dashboard widgets, you also need access to the underlying reports.

Each dashboard has a running user, whose security settings determine which data to display in a dashboard. If the running user is a specific user, all dashboard viewers see data based on the security settings of that user—regardless of their own personal security settings. For this reason, you’ll want to choose the running user wisely, so as not to open up too much visibility. For example, set the sales manager as the running user for a leaderboard for her team. This allows her team members to view the leaderboard for their individual team, but not other teams.
Dynamic dashboards are dashboards for which the running user is always the logged-in user. This way, each user sees the dashboard according to his or her own access level. If you’re concerned about too much access, dynamic dashboards might be the way to go.

# Add Filters
When you’re using the report builder to ask questions about your data, filters allow you to get more specific. 

First, let’s take a high-level look at these features, and then we walk you through how to build a filter.

You can filter the data in a report using the following filter options.

|**Filter Type**|**Description**|
|---------------|---------------|
|**Standard Filter**|Most objects include standard filters. Different objects have different standard filters, but most include the standard filters Show Me and Created Date. Show Me filters the object around common groupings (like My accounts or All accounts). Date Field filters by a field (such as Created Date or Last Activity) and a date range (such as All Time or Last Month).|
|**Field Filter**|Field filters are available for reports, list views, workflow rules, and other areas of the application. For each filter, set the field, operator, and value. To add a field filter, use the search bar in the Filters tab or drag the field from the Fields list.|
|**Filter Logic**|Add Boolean conditions to control how field filters are evaluated. You must add at least 1 field filter before applying filter logic. Filter logic applies to field filters, but not standard filters.|
|**Cross Filter**|Filter a report by a child object using WITH or WITHOUT conditions. Add subfilters to further filter by fields on the child object. For example, if you have a cross filter of Accounts with Opportunities, click Add Opportunity Filter and create the Opportunity Name equals ACME subfilter to include only those opportunities.|
|**Row Limit**|For ungrouped (tabular) reports, select the maximum number of rows to display, choose a field to sort by, and specify the sort order. You can use a tabular report as the source report for a dashboard table or chart component if you limit the number of rows it returns.|

# Use Cross Filters
Now that you’ve built a filter, let’s go to the next level with cross filters. These filter types allow you to extend your reports to objects related to the original objects defined in the report type. Cross filters help you fine-tune your results without writing code or using formulas. The most common use case is exception reporting. Here are some examples that the sales team at Ursa Major Solar has requested.

- **Accounts with Opportunities**: Accounts with opportunities that are stuck in the early stages of the sales cycle. Lance would like to spend the afternoon doing outreach to these accounts to see if he can move them along to the next stages.
- **Stale Opportunities**: Opportunities without activities in the past 90 days. Erin doesn’t want to waste time calling these opportunities.
- **Orphan Contacts**: Contacts without accounts. Lincoln Ulrich, Ursa Major Solar account executive, wants to add these contacts to accounts or scrub them away.

# Use Filter Logic
Filter logic lets you apply filters based on conditions. Say that Erin wants to focus her sales activities this week on all her open opportunities that have a reasonable probability of closing or that have a high enough amount to warrant some extra effort.  