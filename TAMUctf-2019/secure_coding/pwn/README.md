# PWN

## Points
464

## Description
https://gitlab.tamuctf.com/root/pwn

Difficulty: easy

Now that you have broken a PWN challenge it's your turn to fix it!  
  
To solve this challenge you must first fork the challenge and then modify the files in this repository and attempt to fix the vulnerability that you found.  
Everytime you make a commit your files are tested on the backend system. The results can be found under CI/CD->Jobs and then the last test ran.  
If you pass all of the tests the flag will be printed at the bottom of the CI/CD display. Otherwise you will either get an error or statement saying what happened.

## Solution
```c
void echo()
{
	printf("%s", "Enter a word to be echoed:\n");
	char buf[128];
	gets(buf);
	printf("%s\n", buf);
}
```
`gets` is vulnerable to buffer overflow if the user enters a string larger than the buffer. Let's fix it by repeatedly reading a fixed size part of the input.
```c
#include <string.h>

void echo()
{
	printf("%s", "Enter a word to be echoed:\n");
	char buf[128];
	while (fgets(buf, sizeof(buf), stdin) != 0)
	{
		size_t len = strlen(buf);
		if (len == 0)
			break;
		printf("%s", buf);
		if (buf[len-1] == '\n')
			break;
	}
}
```

Commit, push and look at the output of the CI/CD job.
```
{"msg": "Service Check Succeeded After Attack\nflag: gigem{check_that_buffer_size_baby}"}
```

## Flag
`gigem{check_that_buffer_size_baby}`