# What are Rollu-Up Summary Fields?

- Roll-up summary fields calculate values from a set of related records, such as those in a related list. 
- You can create roll-up summary fields that automatically display a value on a master record based on the values of records in a detail record. 
- These detail records must be directly related to the master through a master-detail relationship.
- You define a roll-up summary field on the object that is on the master side of a master-detail relationship. For example, you can create a roll-up summary field on the Account object, summarizing related opportunities:

|**Type**|**Description**|
|--------|---------------|
|**COUNT**|*Totals the number of related records.*|
|**SUM**|*Totals the values in the field you select in the Field to Aggregate option. Only number, currency, and percent fields are available.*|
|**MIN**|*Displays the lowest value of the field you select in the Field to Aggregate option for all directly related records. Only number, currency, percent, date, and date/time fields are available.*|
|**MAX**|*Displays the highest value of the field you select in the Field to Aggregate option for all directly related records. Only number, currency, percent, date, and date/time fields are available.*|

# Validation Rules

- Validation rules verify that data entered by users in records meets the standards you specify before they can save it. 
- A validation rule can contain a formula or expression that evaluates the data in one or more fields and returns a value of “True” or “False.” 
- When the validation rule returns a value of "True", this confirms that the data entered by the user contains an invalid value. 
- Validation rules can also include error messages to display to users when they enter invalid values based on specified criteria. 
- Using these rules effectively contributes to quality data. 
- For example, you can ensure that all phone number fields contain a specified format or that discounts applied to certain products never exceed a defined percentage.
- You can create validation rules for objects, fields, campaign members, or case milestones.