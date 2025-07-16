---
title: Prevent SQLi with Validators and Prepared Statements
publishDate: '2024-09-12T08:39:41.988Z'
description: >-
  Ringkasan singkat artikel tentang How to Prevent SQL Injection Attacks with
  Validators and Prepared Statements in Backend Code.
heroImage: {src: './image.png',color: '#ffffff'}
draft: false
comment: true
---
SQL injection attacks remain one of the most prevalent and dangerous security vulnerabilities in web applications. These attacks allow malicious users to manipulate database queries, potentially compromising sensitive data or altering system functionality. This article discusses the methods to secure your web applications against such threats by incorporating input validation and prepared statements. Using Codey Confectionery, a simple web application as an example, we will demonstrate how these techniques can effectively protect your backend code from SQL injection attempts.

**Theory**

SQL injection occurs when an application dynamically constructs an SQL query using unsanitized or improperly validated user input. In the context of a web application, attackers exploit this vulnerability by injecting malicious SQL code into input fields, allowing them to manipulate queries in unintended ways. For instance, in the example of Codey Confectionery, an insecure SQL query like:
```js
const validator = require('validator');

app.post('/track', (req, res) => {  
  if (validator.isInt(req.body.customerId)) {  
    db.all(  
      "SELECT * FROM Employee WHERE EmployeeId = $customerId",  
      { $customerId: req.body.customerId },  
      (err, rows) => {  
        if (rows) {  
          res.status(200);  
          res.json(rows);  
        } else {  
          res.status(200);  
          res.json({ message: "No employees" });  
        }  
      }  
    );  
  } else {  
    res.json({ message: "Invalid customer ID." });  
  }  
});
```
can be compromised by entering `1' OR '1' = '1`, which would return all employee records instead of just one. To mitigate this risk, two essential techniques can be employed: input validation and prepared statements.

1.  **Input Validation**: Ensuring that user input matches expected formats (e.g., integers for employee IDs) can help reduce vulnerabilities. In this case, using a validation library like `validator` can check if the input is a valid integer before proceeding with the query execution.
2.  **Prepared Statements**: These allow user inputs to be safely incorporated into queries without directly embedding them, preventing SQL code injection. By separating query logic from user inputs through placeholders, malicious SQL input will be treated as data rather than executable code.

By implementing these techniques, you can create a secure backend that prevents attackers from manipulating your database through SQL injection.

## Understanding the Vulnerability

Let’s begin by examining the core issue. Here’s a snippet from the `app.js` file of Codey Confectionery:
```js
app.post('/track', (req, res) => {  
  db.all(  
    "SELECT * FROM Employee WHERE EmployeeId = $customerId",  
    { $customerId: req.body.customerId },  
    (err, rows) => {  
      if (rows) {  
        res.status(200);  
        res.json(rows);  
      } else {  
        res.status(200);  
        res.json({ message: "No employees" });  
      }  
    }  
  );   
}); 
```
This code retrieves employee data based on the `EmployeeId` from a web form. However, this is vulnerable to SQL injection. For example, a malicious user could submit `1' OR '1' = '1` into the form, tricking the database into returning all employee records.

## Step 1: Adding Input Validation

To prevent SQL injection, the first step is to ensure that the form input is valid. In this case, we expect the `EmployeeId` to be an integer. We can use the **validator** library to check if the input is indeed an integer before executing the SQL query.

First, install the validator package:

npm install validator

Then, add the following line at the top of your `app.js` file to require the validator:

const validator = require('validator');

Now, modify the `/track` route to validate the `customerId` before running the SQL query:
```js
app.post('/track', (req, res) => {  
  if (validator.isInt(req.body.customerId)) {  
    // Proceed with query if valid integer  
  } else {  
    res.json({ message: "Invalid customer ID." });  
  }  
});
```
This change ensures that only valid integers are processed, blocking any non-numeric or malicious input that could be used for an SQL injection attack.

## Step 2: Implementing Prepared Statements

Even with validation in place, it’s crucial to use **prepared statements** to prevent SQL injection attacks. Prepared statements allow you to safely pass user input into a query without directly embedding it into the SQL string, making it impossible for malicious users to alter your query logic.

Let’s refactor the SQL query to use a prepared statement:
```js
db.all(  
  "SELECT \* FROM Employee WHERE EmployeeId = $customerId",  
  {  
    $customerId: req.body.customerId  
  },  
  (err, rows) => {  
    if (rows) {  
      res.status(200);  
      res.json(rows);  
    } else {  
      res.status(200);  
      res.json({ message: "No employees" });  
    }  
  }  
);
```
In this query, `$customerId` is a placeholder for the actual `customerId` value. The value is safely injected into the query without the risk of SQL injection, thanks to the use of a prepared statement.

## Full Secure Code

Here is the fully updated route code that includes both validation and prepared statements:
```js
app.post('/track', (req, res) => {  
  if (validator.isInt(req.body.customerId)) {  
    db.all(  
      "SELECT \* FROM Employee WHERE EmployeeId = $customerId",  
      {  
        $customerId: req.body.customerId  
      },  
      (err, rows) => {  
        if (rows) {  
          res.status(200);  
          res.json(rows);  
        } else {  
          res.status(200);  
          res.json({ message: "No employees" });  
        }  
      }  
    );  
  } else {  
    res.json({ message: "Invalid customer ID." });  
  }  
});
```
## Testing the Solution

![](https://cdn-images-1.medium.com/max/800/1*6qU6gNAHaJyKQRxU19_zsg.png)

After implementing these changes, test the application by submitting invalid data and SQL injection attempts. For example:

1.  Try submitting a non-integer value, such as `"abc"`. You should receive an error message: **Invalid customer ID**.
2.  Attempt an SQL injection with `"1' OR '1' = '1"`. The query will no longer be vulnerable, and no sensitive data will be exposed.

## Conclusion

By adding input validation and using prepared statements, you can significantly reduce the risk of SQL injection attacks. These are essential steps in securing your backend code and ensuring that user input is properly sanitized before interacting with your database.

With these changes, Codey Confectionery is now protected from SQL injection vulnerabilities. Make sure to apply these best practices to all user input fields in your application to keep it secure.

* * *

**Thanks to**: [Codecademy](https://www.codecademy.com/courses/defending-express-applications-from-sql-injection-xss-csrf-attacks/projects/codeys-confectionery-sql-injection)
