# 042

## Points
484

## Description
Cheers for actual assembly!

\#medium

[reversing3.s](https://tamuctf.com/files/9cca9cf5fd2409ddb51db4841ee97617/reversing3.s)

## Solution
Let's look at the [code](reversing3.s). This is the format for printing the flag.
```
L_.str.2:                               ## @.str.2
	.asciz	"gigem{%s}\n"
```
And this is how it's called.
```
	callq	_printf
	leaq	L_.str.2(%rip), %rdi
	leaq	-16(%rbp), %rsi
```
Now what's at `-16(%rbp)`?
```
	movb	$65, -16(%rbp)
	movb	$53, -15(%rbp)
	movb	$53, -14(%rbp)
	movb	$51, -13(%rbp)
	movb	$77, -12(%rbp)
	movb	$98, -11(%rbp)
	movb	$49, -10(%rbp)
	movb	$89, -9(%rbp)
```
Convert these bytes to ASCII characters.

## Flag
`gigem{A553Mb1Y}`