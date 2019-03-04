# -.-

## Points
391

## Description
To 1337-H4X0R:

Our coworker Bob loves a good classical cipher. Unfortunately, he also loves to send everything encrypted with these ciphers. Can you go ahead and decrypt this for me?

Difficulty: easy

[flag.txt](https://tamuctf.com/files/cd5fef538fad2500c30c4ea389c50244/flag.txt)

## Solution
[flag.txt](flag.txt) looks like Morse Code:
- replace `dah` with `-`
- replace `dit` and `di` with `.`


```sh
λ sed s/-//g;s/dah/-/g;s/dit/./g;s/di/./g; flag.txt
```
Feed the result into [morse code translator](https://www.dcode.fr/morse-code).
```
0X57702A6C58744751386538716E6D4D59552A737646486B6A49742A5251264A705A766A6D2125254B446B6670235E4E39666B346455346C423372546F5430505A516D4351454B5942345A4D762A21466B386C25626A716C504D6649476D612525467A4720676967656D7B433169634B5F636C31434B2D7930755F683476335F6D3449317D20757634767A4B5A7434796F6D694453684C6D385145466E5574774A404E754F59665826387540476E213125547176305663527A56216A217675757038426A644E49714535772324255634555A4F595A327A37543235743726784C40574F373431305149
```
Notice that it starts with `0x` and then there are only letters `[A-E]`, so it's probably in hexadecimal. Let's feed it to [Hex to Text converter](https://codebeautify.org/hex-string-converter).
```
Wp*lXtGQ8e8qnmMYU*svFHkjIt*RQ&JpZvjm!%%KDkfp#^N9fk4dU4lB3rToT0PZQmCQEKYB4ZMv*!Fk8l%bjqlPMfIGma%%FzG gigem{C1icK_cl1CK-y0u_h4v3_m4I1} uv4vzKZt4yomiDShLm8QEFnUtwJ@NuOYfX&8u@Gn!1%Tqv0VcRzV!j!vuup8BjdNIqE5w#$%V4UZOYZ2z7T25t7&xL@WO7410QI
```

## Flag
`gigem{C1icK_cl1CK-y0u_h4v3_m4I1}`