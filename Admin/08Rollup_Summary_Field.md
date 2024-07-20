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