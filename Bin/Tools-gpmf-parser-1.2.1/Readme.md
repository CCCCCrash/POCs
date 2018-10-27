
use the demo code and find a OOB write bug in GPMF_mp4reader.c:342


==942== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.
==942== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==942== Command: ./gpmfdemo ../SIGSEGV.PC.46ac9e.STACK.165cdfbb18.CODE.128.ADDR.(nil).INSTR.mov____%r9d,(%rax,%rdi,4).fuzz
==942==
==942== Warning: set address range perms: large range [0x5604040, 0x33c74a90) (undefined)
==942== Invalid write of size 4
==942==    at 0x4413DE: OpenMP4Source (GPMF_mp4reader.c:342)
==942==    by 0x400C92: main (GPMF_demo.c:48)
==942==  Address 0x233c74a8c is not stack'd, malloc'd or (recently) free'd
==942==
==942==
==942== Process terminating with default action of signal 11 (SIGSEGV)
==942==  Access not within mapped region at address 0x233C74A8C
==942==    at 0x4413DE: OpenMP4Source (GPMF_mp4reader.c:342)
==942==    by 0x400C92: main (GPMF_demo.c:48)
==942==  If you believe this happened as a result of a stack
==942==  overflow in your program's main thread (unlikely but
==942==  possible), you can try to increase the size of the
==942==  main thread stack using the --main-stacksize= flag.
==942==  The main thread stack size used in this run was 8388608.
==942==
==942== HEAP SUMMARY:
==942==     in use at exit: 778,505,432 bytes in 3 blocks
==942==   total heap usage: 5 allocs, 2 frees, 778,509,540 bytes allocated
==942==
==942== LEAK SUMMARY:
==942==    definitely lost: 96 bytes in 1 blocks
==942==    indirectly lost: 0 bytes in 0 blocks
==942==      possibly lost: 778,504,784 bytes in 1 blocks
==942==    still reachable: 552 bytes in 1 blocks
==942==         suppressed: 0 bytes in 0 blocks
==942== Rerun with --leak-check=full to see details of leaked memory
==942==
==942== For counts of detected and suppressed errors, rerun with: -v
==942== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
Segmentation fault


ubuntu@VM-12-40-ubuntu:~/fuzz/gpmf-parser-clang/demo-sanitize$ ./gpmfdemo ../SIGSEGV.PC.46ac9e.STACK.165cdfbb18.CODE.128.ADDR.\(nil\).INSTR.mov____%r9d\,\(%rax\,%rdi\,4\).fuzz
ASAN:DEADLYSIGNAL
=================================================================
==24135==ERROR: AddressSanitizer: SEGV on unknown address 0x7f88796ff24c (pc 0x00000054bd4e bp 0x00008b99c294 sp 0x7fff11184c70 T0)
==24135==The signal is caused by a WRITE memory access.
    #0 0x54bd4d  (/home/ubuntu/fuzz/gpmf-parser-clang/demo-sanitize/gpmfdemo+0x54bd4d)
    #1 0x419a82  (/home/ubuntu/fuzz/gpmf-parser-clang/demo-sanitize/gpmfdemo+0x419a82)
    #2 0x7f867c05882f  (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #3 0x41b078  (/home/ubuntu/fuzz/gpmf-parser-clang/demo-sanitize/gpmfdemo+0x41b078)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ubuntu/fuzz/gpmf-parser-clang/demo-sanitize/gpmfdemo+0x54bd4d)
==24135==ABORTING