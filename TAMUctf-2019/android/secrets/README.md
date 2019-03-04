# Secrets

## Points
482

## Description
Can you find my secrets?

[howdyapp.apk](https://tamuctf.com/files/5c2386d25b375771f754d1669e54aff2/howdyapp.apk)

## Solution
Use [apktool](https://github.com/iBotPeaches/Apktool) to decompile the apk.
```sh
λ java -jar apktool_2.3.4.jar d howdyapp.apk
```
Open `howdyapp\res\values\strings.xml`.
```xml
    <string name="flag">Z2lnZW17aW5maW5pdGVfZ2lnZW1zfQ==</string>
```
This is a string encoded in base64. You can decode it using https://www.base64decode.org/ or `base64` command.
```sh
λ echo Z2lnZW17aW5maW5pdGVfZ2lnZW1zfQ== | base64 -di
gigem{infinite_gigems}
```

## Flag
`gigem{infinite_gigems}`