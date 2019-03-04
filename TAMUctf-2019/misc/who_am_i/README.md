# Who am I?

## Points
144

## Description
What is the A record for tamuctf.com?
(Not in standard gigem{flag} format)

Difficulty: easy

## Solution
```sh
$ dig A tamuctf.com

; <<>> DiG 9.11.5-P1-1-Debian <<>> A tamuctf.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14536
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;tamuctf.com.                   IN      A

;; ANSWER SECTION:
tamuctf.com.            52305   IN      A       52.33.57.247

;; Query time: 25 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Feb 24 18:50:29 STD 2019
;; MSG SIZE  rcvd: 56
```

## Flag
`52.33.57.247`