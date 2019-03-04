# SQL

## Points
492

## Description
https://gitlab.tamuctf.com/root/sql

Now that you have broken the SQL Injection challenge it's your turn to fix it!  
  
To solve this challenge you must first fork the challenge and then modify the files in this repository and attempt to fix the vulnerability that you found.  
Everytime you make a commit your files are tested on the backend system. The results can be found under CI/CD->Jobs and then the last test ran.  
If you pass all of the tests the flag will be printed at the bottom of the CI/CD display. Otherwise you will either get an error or statement saying what happened.

## Solution
Clone the repository and look at `login.php`.
```php
    $user = $_POST['username'];
    $pass = $_POST['password'];
    $sql = "SELECT * FROM login WHERE User='$user' AND Password='$pass'";
```
The best way to [prevent the SQL injection](http://bobby-tables.com/php) is to use bound parameters, but quick escaping of the input will do the job as well.
```php
    $user = $conn->real_escape_string($_POST['username']);
    $pass = $conn->real_escape_string($_POST['password']);
```
Commit, push and look at the output of the CI/CD job:
```sh
$ chmod +x ./tests/entry.sh
$ ./tests/entry.sh
 * Starting MySQL database server mysqld
   ...done.
 * Stopping Apache httpd web server apache2
 * 
 * Starting Apache httpd web server apache2
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.17.0.3. Set the 'ServerName' directive globally to suppress this message
 * 
172.17.0.3
Pushing: {'serviceHost': '172.17.0.3', 'userInfo': u'0f347094f1298b68dd8d3d5a36c6727cf3ebbefea20ad62aa78ad1cb12629607', 'chal': 'SQL'}
Service Check Succeeded After Attack
flag: gigem{the_best_damn_sql_anywhere}
Job succeeded
```

## Flag
`gigem{the_best_damn_sql_anywhere}`