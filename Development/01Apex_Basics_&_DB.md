# What is Apex?
Apex is a programming language that uses Java-like syntax and acts like database stored procedures. Apex enables developers to add business logic to system events, such as button clicks, updates of related records, and Visualforce pages.

**Apex is**:
- Hosted
- Object oriented 
- Strongly typed
- Mutitenant aware
- Integrated with the database
- Data focused
- Easy to use & test
- Versioned

**Language constructs that Apex supports**:
- Classes, interfaces, properties, and collections (lists, maps, and sets).
- Object and array notation.
- Expressions, variables, and constants.
- Conditional statements (if-then-else) and control flow statements (for loops and while loops).
- Cloud development as Apex is stored, compiled, and executed in the cloud.
- Triggers, which are similar to triggers in database systems.
- Database statements that allow you to make direct database calls and query languages to query and search data.
- Transactions and rollbacks.
- The global access modifier, which is more permissive than the public modifier and allows access across namespaces and applications.
- Versioning of custom code.
*Apex is case sensitive language.*

# Data Types
1. **Primitive**
- Integer, 
- Double, 
- Long, 
- Date, 
- Datetime, 
- String, 
- ID, 
- Boolean
2. **sObject**
3. **Collection**
- Lists,
- Sets,
- Maps
4. **Enum**

# Apex Collections: List
Lists hold an ordered collection of data of the same type.
```List<String> colors = new List<String>();```

**Adding elements in a List:**

\```
// Create a list and add elements to it in one step
List<String> colors = new List<String> { 'red', 'green', 'blue' };
// Add elements to a list after it has been created
List<String> moreColors = new List<String>();
moreColors.add('orange');
moreColors.add('purple');
\```

**Iteration over a List:**
\```
// Get elements from a list
String color1 = moreColors.get(0);
String color2 = moreColors[0];
System.assertEquals(color1, color2);
// Iterate over a list to read elements
System.debug('Print out the colors in moreColors:');
for(String color : moreColors) {
    // Write value to the debug log
    System.debug(color);
}
\```

# Apex Classes
One of the benefits of Apex classes is code reuse. Class methods can be called by triggers and other classes.
