# Not Another SQLi Challenge

## Points
307

## Description
http://web1.tamuctf.com

Difficulty: easy

![index](img/Central_Authentication_Service_RC1.2_1.png)

## Solution
As the name suggests, this will be an [SQL injection](https://en.wikipedia.org/wiki/SQL_injection) challenge.

Enter `' or '1'='1` in both fields.

![SQL injection](img/Central_Authentication_Service_RC1.2_2.png)

Voilà! Access granted.

![Access granted](img/web1.tamuctf.com_web_login.php.png)

## Flag
`gigem{f4rm3r5_f4rm3r5_w3'r3_4ll_r16h7}`