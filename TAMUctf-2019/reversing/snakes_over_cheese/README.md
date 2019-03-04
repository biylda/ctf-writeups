# Snakes over cheese

## Points
376

## Description
easy

What kind of file is this?

[reversing2.pyc](https://tamuctf.com/files/9a4c21a5f7a72794def3fabb2d3f9d51/reversing2.pyc)

## Solution
It's compiled python code. Let's decompile it. Use e.g. https://sourceforge.net/projects/easypythondecompiler/.

```python
# Embedded file name: reversing2.py
from datetime import datetime
Fqaa = [102,
 108,
 97,
 103,
 123,
 100,
 101,
 99,
 111,
 109,
 112,
 105,
 108,
 101,
 125]
XidT = [83,
 117,
 112,
 101,
 114,
 83,
 101,
 99,
 114,
 101,
 116,
 75,
 101,
 121]

def main():
    print 'Clock.exe'
    input = raw_input('>: ').strip()
    kUIl = ''
    for i in XidT:
        kUIl += chr(i)

    if input == kUIl:
        alYe = ''
        for i in Fqaa:
            alYe += chr(i)

        print alYe
    else:
        print datetime.now()


if __name__ == '__main__':
    main()
```

As you can see, if our input is `XidT`, it will print the flag `Fqaa`. Let's launch it interactively and get the strings.

```sh
λ python2 -i reversing2.pyc
Clock.exe
>:

2019-02-24 17:00:23.820048
>>> print ''.join([chr(i) for i in XidT])
print ''.join([chr(i) for i in XidT])
SuperSecretKey
>>> print ''.join([chr(i) for i in Fqaa])
print ''.join([chr(i) for i in Fqaa])
flag{decompile}
>>>
```

## Flag
`flag{decompile}`