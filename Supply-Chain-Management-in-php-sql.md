# Supply-Chain-Management-in-php-sql

https://code-projects.org/supply-chain-management-in-php-css-js-and-mysql-free-download/

## NAME OF AFFECTED PRODUCT(S)

**Supply Chain Management**

## Vendor Homepage

https://code-projects.org/supply-chain-management-in-php-css-js-and-mysql-free-download/

##  **Manufacturers sites**

https://code-projects.org/

## AFFECTED  VERSION(S)

### Vulnerable File

edit_manufacturer.php

### VERSION(S)

-  v1.0

### Software Link

https://download.code-projects.org/details/adc6862d-bae0-4b2e-8033-37ac6e72d9c2

## PROBLEM TYPE

network remote.

## Vulnerability Type

sql injection

## Root Cause

edit_manufacturer.php file, SQL injection is used to obtain database information.

## Impact

## **Description of the vulnerability**

### edit_manufacturer.php

source code，the  id parameter is not filtered and concatenated into the SQL statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                               

```php
			$id = $_GET['id'];
			$query_selectManDetails = "SELECT * FROM manufacturer WHERE man_id='$id'";
```

![image-20240925144230627](C:\Users\13756\AppData\Roaming\Typora\typora-user-images\image-20240925144230627.png)

## **Vulnerability recurrence**

### **POC**

```

```



