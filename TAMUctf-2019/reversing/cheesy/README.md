# Cheesy

## Points
307

## Description
easy

Where will you find the flag?

[reversing1](https://tamuctf.com/files/3d3fb75bb5cfe9b8af5b39a96dde03dd/reversing1)

## Solution
Looking at the content of [reversing1](reversing1) we discover that it's an executable. Let's extract some strings.
```sh
λ strings reversing1

Strings v2.53 - Search for ANSI and Unicode strings in binary images.
Copyright (C) 1999-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

ELF
/lib64/ld-linux-x86-64.so.2
GNU
GNU
?cL
CyIk
libstdc++.so.6
__gmon_start__
_Jv_RegisterClasses
_ITM_deregisterTMCloneTable
_ITM_registerTMCloneTable
_ZNSaIcED1Ev
_ZNSt8ios_base4InitD1Ev
__gxx_personality_v0
_ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
_ZNSaIcEC1Ev
_ZNSt8ios_base4InitC1Ev
_ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
_ZSt4cout
libgcc_s.so.1
_Unwind_Resume
libc.so.6
__stack_chk_fail
__cxa_atexit
__libc_start_main
GCC_3.0
GLIBC_2.4
GLIBC_2.2.5
CXXABI_1.3
GLIBCXX_3.4.21
GLIBCXX_3.4
P&y
  `
( `
0 `
8 `
@ `
H `
P `
X `
` `
h `
p `
PTI
UH-
HdH
dH3
H[]
AWAVA
AUATL
t 1
[]A\A]A^A_
QUFBQUFBQUFBQUFBQUFBQQ==
Hello! I bet you are looking for the flag..
I really like basic encoding.. can you tell what kind I used??
RkxBR2ZsYWdGTEFHZmxhZ0ZMQUdmbGFn
Q2FuIHlvdSByZWNvZ25pemUgYmFzZTY0Pz8=
Z2lnZW17M2E1eV9SM3YzcjUxTjYhfQ==
WW91IGp1c3QgbWlzc2VkIHRoZSBmbGFn
;*3$"
zPLR
GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.11) 5.4.0 20160609
x `
x `
x `
crtstuff.c
__JCR_LIST__
deregister_tm_clones
__do_global_dtors_aux
completed.7594
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
reversing1.cpp
_ZStL8__ioinit
_Z41__static_initialization_and_destruction_0ii
_GLOBAL__sub_I_main
__FRAME_END__
__JCR_END__
__GNU_EH_FRAME_HDR
_GLOBAL_OFFSET_TABLE_
__init_array_end
__init_array_start
_DYNAMIC
__libc_csu_fini
__gmon_start__
_Jv_RegisterClasses
_ZNSt8ios_base4InitC1Ev@@GLIBCXX_3.4
__libc_start_main@@GLIBC_2.2.5
__cxa_atexit@@GLIBC_2.2.5
_ZNSt8ios_base4InitD1Ev@@GLIBCXX_3.4
_ITM_deregisterTMCloneTable
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@@GLIBCXX_3.4
_IO_stdin_used
_ITM_registerTMCloneTable
__data_start
_ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev@@GLIBCXX_3.4.21
__TMC_END__
_ZSt4cout@@GLIBCXX_3.4
__dso_handle
__libc_csu_init
__bss_start
__stack_chk_fail@@GLIBC_2.4
_ZNSaIcED1Ev@@GLIBCXX_3.4
_ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_@@GLIBCXX_3.4.21
_edata
_ZNSaIcEC1Ev@@GLIBCXX_3.4
__gxx_personality_v0@@CXXABI_1.3
_Unwind_Resume@@GCC_3.0
.symtab
.strtab
.shstrtab
.interp
.note.ABI-tag
.note.gnu.build-id
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.plt.got
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.gcc_except_table
.init_array
.fini_array
.jcr
.dynamic
.got.plt
.data
.bss
.comment
x `
```

The encoded strings are base64, let's decode them using https://www.base64decode.org/ or `base64` command.
```
FLAGflagFLAGflagFLAGflag
Can you recognize base64??
gigem{3a5y_R3v3r51N6!}
You just missed the flag
```

## Flag
`gigem{3a5y_R3v3r51N6!}`