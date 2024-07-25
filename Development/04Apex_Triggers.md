Apex triggers enable you to perform custom actions before or after events to records in Salesforce, such as insertions, updates, or deletions. Just like database systems support triggers, Apex provides trigger support for managing records.

Typically, you use triggers to perform operations based on specific conditions, to modify related records or restrict certain operations from happening. You can use triggers to do anything you can do in Apex, including executing SOQL and DML or calling custom Apex methods.

Use triggers to perform tasks that can’t be done by using the point-and-click tools in the Salesforce user interface. For example, if validating a field value or updating a field on a record, use validation rules and flows. Use Apex triggers if performance and scale is important, if your logic is too complex for the point-and-click tools, or if you're executing CPU-intensive operations.

Triggers can be defined for top-level standard objects, such as Account or Contact, custom objects, and some standard child objects. Triggers are active by default when created. Salesforce automatically fires active triggers when the specified database events occur.

# Trigger Syntax

```
trigger TriggerName on ObjectName (trigger_events) {
   code_block
}
```

To execute a trigger before or after insert, update, delete, and undelete operations, specify multiple trigger events in a comma-separated list. The events you can specify are:

- `before insert`
- `before update`
- `before delete`
- `after insert`
- `after update`
- `after delete`
- `after undelete`

# Types of Triggers
There are `two` types of triggers.

1. `Before triggers` are used to update or validate record values before they’re saved to the database.
2. `After triggers` are used to access field values that are set by the system (such as a record's Id or LastModifiedDate field), and to affect changes in other records. The records that fire the after trigger are read-only.

# Using Context Variables
To access the records that caused the trigger to fire, use context variables. For example, Trigger.new contains all the records that were inserted in insert or update triggers. Trigger.old provides the old version of sObjects before they were updated in update triggers, or a list of deleted sObjects in delete triggers. Triggers can fire when one record is inserted, or when many records are inserted in bulk via the API or Apex. Therefore, context variables, such as Trigger.new, can contain only one record or multiple records. You can iterate over Trigger.new to get each individual sObject.
|**Variable**|**Usage**|
|------------|---------|
|`isExecuting`|Returns true if the current context for the Apex code is a trigger, not a Visualforce page, a Web service, or an `executeanonymous()` API call.|
|`isInsert`|Returns `true` if this trigger was fired due to an insert operation, from the Salesforce user interface, Apex, or the API.|
|`isUpdate`|Returns `true` if this trigger was fired due to an update operation, from the Salesforce user interface, Apex, or the API.|
|`isDelete`|Returns `true` if this trigger was fired due to a delete operation, from the Salesforce user interface, Apex, or the API.|
|`isBefore`|Returns `true` if this trigger was fired before any record was saved.|
|`isAfter`|Returns `true` if this trigger was fired after all records were saved.| 
|`isUndelete`|Returns `true` if this trigger was fired after a record is recovered from the Recycle Bin.This recovery can occur after an undelete operation from the Salesforce user interface, Apex, or the API.|
|`new`|Returns a list of the new versions of the sObject records.This sObject list is only available in `insert`, `update`, and undelete triggers, and the records can only be modified in before triggers.|
|`newMap`|A map of IDs to the new versions of the sObject records.This map is only available in `before update`, `after insert`, `after update`, and `after undelete` triggers.|
|`old`|Returns a list of the old versions of the sObject records.This sObject list is only available in `update` and `delete` triggers.|
|`oldMap`|A map of IDs to the old versions of the sObject records.This map is only available in `update` and `delete` triggers.|
|`operationType`|Returns an enum of type System.TriggerOperation corresponding to the current operation.Possible values of the `System.TriggerOperation` enum are: `BEFORE_INSERT`, `BEFORE_UPDATE`, `BEFORE_DELETE`, `AFTER_INSERT`, `AFTER_UPDATE`, `AFTER_DELETE`, and `AFTER_UNDELETE`. If you vary your programming logic based on different trigger types, consider using the switch statement with different permutations of unique trigger execution enum states.|
|`size`|The total number of records in a trigger invocation, both old and new.|

# Calling a Class Method from a Trigger
You can call public utility methods from a trigger. Calling methods of other classes enables code reuse, reduces the size of your triggers, and improves maintenance of your Apex code. It also allows you to use object-oriented programming.
```
public class EmailManager {
    // Public method
    public static void sendMail(String address, String subject, String body) {
        // Create an email message object
        Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
        String[] toAddresses = new String[] {address};
        mail.setToAddresses(toAddresses);
        mail.setSubject(subject);
        mail.setPlainTextBody(body);
        // Pass this email message to the built-in sendEmail method
        // of the Messaging class
        Messaging.SendEmailResult[] results = Messaging.sendEmail(
                                  new Messaging.SingleEmailMessage[] { mail });
        // Call a helper method to inspect the returned results
        inspectResults(results);
    }
    // Helper method
    private static Boolean inspectResults(Messaging.SendEmailResult[] results) {
        Boolean sendResult = true;
        // sendEmail returns an array of result objects.
        // Iterate through the list to inspect results.
        // In this class, the methods send only one email,
        // so we should have only one result.
        for (Messaging.SendEmailResult res : results) {
            if (res.isSuccess()) {
                System.debug('Email sent successfully');
            }
            else {
                sendResult = false;
                System.debug('The following errors occurred: ' + res.getErrors());
            }
        }
        return sendResult;
    }
}
```
# Adding Related Records
Triggers are often used to access and manage records related to the records in the trigger context—the records that caused this trigger to fire.
```
trigger AddRelatedRecord on Account(after insert, after update) {
    List<Opportunity> oppList = new List<Opportunity>();
    // Get the related opportunities for the accounts in this trigger
    Map<Id,Account> acctsWithOpps = new Map<Id,Account>(
        [SELECT Id,(SELECT Id FROM Opportunities) FROM Account WHERE Id IN :Trigger.new]);
    // Add an opportunity for each account if it doesn't already have one.
    // Iterate through each account.
    for(Account a : Trigger.new) {
        System.debug('acctsWithOpps.get(a.Id).Opportunities.size()=' + acctsWithOpps.get(a.Id).Opportunities.size());
        // Check if the account already has a related opportunity.
        if (acctsWithOpps.get(a.Id).Opportunities.size() == 0) {
            // If it doesn't, add a default opportunity
            oppList.add(new Opportunity(Name=a.Name + ' Opportunity',
                                       StageName='Prospecting',
                                       CloseDate=System.today().addMonths(1),
                                       AccountId=a.Id));
        }
    }
    if (oppList.size() > 0) {
        insert oppList;
    }
}
```
# Using Trigger Exceptions
You sometimes need to add restrictions on certain database operations, such as preventing records from being saved when certain conditions are met. To prevent saving records in a trigger, call the `addError()` method on the sObject in question. The `addError()` method throws a fatal error inside a trigger. The error message is displayed in the user interface and is logged.
```
trigger AccountDeletion on Account (before delete) {
    // Prevent the deletion of accounts if they have related opportunities.
    for (Account a : [SELECT Id FROM Account
                     WHERE Id IN (SELECT AccountId FROM Opportunity) AND
                     Id IN :Trigger.old]) {
        Trigger.oldMap.get(a.Id).addError(
            'Cannot delete account with related opportunities.');
    }
}
```
# Triggers and Callouts
Apex allows you to make calls to and integrate your Apex code with external Web services. Apex calls to external Web services are referred to as callouts. For example, you can make a callout to a stock quote service to get the latest quotes. When making a callout from a trigger, the callout must be done asynchronously so that the trigger process doesn’t block you from working while waiting for the external service's response. The asynchronous callout is made in a background process, and the response is received when the external service returns it.

To make a callout from a trigger, call a class method that executes asynchronously. Such a method is called a future method and is annotated with `@future(callout=true)`.
```
public class CalloutClass {
    @future(callout=true)
    public static void makeCallout() {
        HttpRequest request = new HttpRequest();
        // Set the endpoint URL.
        String endpoint = 'http://yourHost/yourService';
        request.setEndPoint(endpoint);
        // Set the HTTP verb to GET.
        request.setMethod('GET');
        // Send the HTTP request and get the response.
        HttpResponse response = new HTTP().send(request);
    }
}
```
This example shows the trigger that calls the method in the class to make a callout asynchronously.
```
trigger CalloutTrigger on Account (before insert, before update) {
    CalloutClass.makeCallout();
}
```