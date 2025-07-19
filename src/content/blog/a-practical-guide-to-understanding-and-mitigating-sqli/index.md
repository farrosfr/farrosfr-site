---
title: A Practical Guide to Understanding and Mitigating SQLi
publishDate: '2025-01-02T02:48:26.443Z'
description: >-
  A Practical Guide to Understanding and Mitigating SQL Injection Risks.
tags: [SQLi, Cybersecurity, Web Security, Vulnerability, PHP]
heroImage: { src: './image.png', color: '#223655' }
draft: false
comment: true
---
## Introduction

SQL Injection (SQLi) is a critical web security vulnerability that allows attackers to manipulate SQL queries executed by an application. This attack occurs when user inputs are improperly sanitized and directly embedded into SQL statements, enabling attackers to execute arbitrary SQL commands. SQLi can lead to unauthorized access, data theft, or even complete database compromise.

* * *

## How SQL Injection Works

SQL Injection exploits the way SQL queries are constructed. When user inputs are concatenated directly into a query without proper validation, attackers can inject malicious SQL code. For example:

## Vulnerable Code Example (PHP)
```sql
$username = $\_POST\['username'\];  
$password = $\_POST\['password'\];  
$query = "SELECT \* FROM users WHERE username = '$username' AND password = '$password'";  
$result = mysqli\_query($connection, $query);
```
If an attacker inputs:

```sql
\- username: admin

\- password: ‘ OR ‘1’=’1
```

The resulting query becomes:

```sql
SELECT \* FROM users WHERE username \= 'admin' AND password \= '' OR '1'\='1';
```

Here, ‘1’=’1' always evaluates to true, bypassing authentication.

* * *

## Types of SQL Injection Attacks

1\. Classic SQL Injection:

\- Directly injects malicious SQL commands into user input fields.

\- Example payload: ‘ OR ‘1’=’1'; —

2\. Union-Based SQL Injection:

\- Exploits the UNION operator to extract data from other tables.

\- Example payload:

' UNION SELECT username, password FROM admin\_users;--

3\. Boolean-Based Blind SQL Injection:

\- Uses true/false conditions to infer information.

\- Example payload:

`' AND 1=1;-- (true)`  
     `' AND 1\=2;\-- (false)`

4\. Time-Based Blind SQL Injection:

\- Exploits database functions that cause delays to infer data.

\- Example payload:

`' OR IF(1=1, SLEEP(5), 0);--`

5\. Error-Based SQL Injection:

\- Leverages database error messages to gather information.

\- Example payload:

`' AND 1=CONVERT(int, (SELECT @@version));--`

* * *

## Real-World Consequences of SQL Injection

\- Data Theft: Attackers can extract sensitive data like usernames, passwords, or financial records.

\- Data Manipulation: Altering or deleting records, such as voiding transactions or changing account balances.

\- Privilege Escalation: Gaining administrative access by injecting commands that modify user privileges.

\- Denial of Service (DoS): Dropping tables or shutting down the database server.

\- System Compromise: Executing OS-level commands through advanced techniques.

* * *

## Preventing SQL Injection

### 1\. Parameterized Queries (Prepared Statements)

Parameterized queries separate data from code, ensuring user inputs are treated as literals rather than executable commands.

Safe Code Example (PHP):
```sql
$stmt = $connection\->prepare("SELECT \* FROM users WHERE username = ? AND password = ?");  
$stmt\->bind\_param("ss", $username, $password);  
$stmt\->execute();
```
This approach prevents attackers from altering the query structure.

### 2\. Input Validation and Sanitization

\- Validate user inputs for expected formats (e.g., numeric fields should only accept numbers).

\- Reject inputs containing special characters like ‘, — , or ;.

### 3\. Escaping Special Characters

Use database-specific escaping functions to neutralize special characters in user inputs.

Example in PHP:

$username = mysqli\_real\_escape\_string($connection, $\_POST\['username'\]);

### 4\. Stored Procedures

Stored procedures execute predefined SQL code on the server side, reducing the risk of injection if properly implemented.

Example (MySQL):
```sql
CREATE PROCEDURE GetUser(IN username VARCHAR(50), IN password VARCHAR(50))  
BEGIN  
    SELECT \* FROM users WHERE username \= username AND password \= password;  
END;
```
### 5\. Least Privilege Principle

Restrict database user permissions to only what is necessary for the application. For example:

\- The application should not have permissions to drop tables or execute administrative commands.

### 6\. Web Application Firewalls (WAF)

Deploy a WAF to monitor and block malicious requests containing known SQL injection patterns.

### 7\. Continuous Security Testing

Regularly perform penetration testing and use automated tools to identify vulnerabilities in your application.

* * *

## Advanced Techniques for Mitigation

### Query Parameterization in Different Languages

*   PHP:
```php
$stmt = $dbh\->prepare("SELECT \* FROM users WHERE id = ?");
```
*   Python:
```python
cursor.execute("SELECT \* FROM users WHERE id = %s", (user\_id,))
```
*   Java:
```js
PreparedStatement ps \= conn.prepareStatement("SELECT \* FROM users WHERE id = ?");
```
### Escaping User Inputs for Specific Databases

*   MySQL: Use mysql\_real\_escape\_string() to escape special characters in input strings.
*   PostgreSQL: Use pg\_escape\_string() to properly handle input.
*   SQLite: Use sqlite\_escape\_string() for input sanitization.

* * *

## Common Mistakes in Mitigation

1\. Relying on Client-Side Validation:

\- Attackers can bypass client-side checks using tools like Burp Suite or directly modifying HTTP requests.

2\. Using Blacklists for Input Validation:

\- Blacklists are incomplete and can be bypassed with creative payloads.

3\. Improperly Written Stored Procedures:

\- Stored procedures must also validate inputs; otherwise, they remain vulnerable.

* * *

## Safe Example

Here is a safe way to implement and run code using prepared statements with MySQLi, the following example is using a simple PHP web page with a form to simulate a login process. The form will allow you to enter a username and password, and the PHP script will handle the request and check the credentials against a MySQL database:

### 1\. HTML Form and PHP Code (Single File)

Save this code in a file, e.g., login.php:
```php
<?php  
// Handle form submission  
if ($\_SERVER\['REQUEST\_METHOD'\] === 'POST') {  
    // Database connection  
    $connection = new mysqli('localhost', 'your\_db\_user', 'your\_db\_password', 'your\_db\_name');  
  
    // Check for connection errors  
    if ($connection\->connect\_error) {  
        die("Connection failed: " . $connection\->connect\_error);  
    }  
  
    // Get username and password from POST request  
    $username = $\_POST\['username'\];  
    $password = $\_POST\['password'\];  
  
    // Prepare and execute query  
    $stmt = $connection\->prepare("SELECT \* FROM users WHERE username = ? AND password = ?");  
    $stmt\->bind\_param("ss", $username, $password);  
    $stmt\->execute();  
    $result = $stmt\->get\_result();  
  
    // Check login result  
    if ($result\->num\_rows > 0) {  
        $message = "Login successful!";  
    } else {  
        $message = "Invalid username or password.";  
    }  
  
    // Close the statement and connection  
    $stmt\->close();  
    $connection\->close();  
}  
?><!DOCTYPE html\>  
<html lang\="en"\>  
<head\>  
    <meta charset\="UTF-8"\>  
    <meta name\="viewport" content\="width=device-width, initial-scale=1.0"\>  
    <title\>Login Simulation</title\>  
</head\>  
<body\>  
    <h1\>Login Simulation</h1\>    <?php if (!empty($message)): ?>        <p\><?php echo htmlspecialchars($message); ?></p\>    <?php endif; ?>    <form method\="POST" action\=""\>  
        <label for\="username"\>Username:</label\>  
        <input type\="text" id\="username" name\="username" required\>  
        <br\><br\>  
        <label for\="password"\>Password:</label\>  
        <input type\="password" id\="password" name\="password" required\>  
        <br\><br\>  
        <button type\="submit"\>Login</button\>  
    </form\>  
</body\>  
</html\>
```
### 2\. Instructions to Simulate the Web Application

1\. Create a Database and Table: Run this SQL to create a database and a table for testing:
``` sql
CREATE DATABASE test\_db;  
USE test\_db;  
  
CREATE TABLE users (  
    id INT AUTO\_INCREMENT PRIMARY KEY,  
    username VARCHAR(50) NOT NULL,  
    password VARCHAR(255) NOT NULL  
);  
  
INSERT INTO users (username, password) VALUES ('testuser', 'testpassword');
```
2\. Replace Database Credentials: Update the mysqli connection code in the PHP script:
``` sql
$connection = new mysqli('localhost', 'root', 'your password', 'test\_db');
```
3\. Run a Local PHP Server: Save the file as login.php and start a PHP server in the directory where it is saved:
``` bash
php -S localhost:8000
```
4\. Access the Application in a Browser: Open a browser and go to [http://localhost:8000/login.php.](http://localhost:8000/login.php.)

5\. Test the Login:

*   Enter the username testuser and password testpassword to log in successfully.
*   Try invalid credentials to see the error message.

## Conclusion

SQL Injection is a powerful attack vector with potentially devastating consequences if left unaddressed. By adopting best practices such as parameterized queries, input validation, and least privilege principles, developers can effectively mitigate this threat and secure their applications against exploitation.
