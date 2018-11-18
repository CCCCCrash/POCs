just as pic show   
  
![the pic](https://github.com/CCCCCrash/POCs/blob/master/Bin/Tools-libansilove-1.0.0/poc.png)  
  
when the libansilove parser crafted file, it will cause a OOB if the seqTok assignned wrong   
  
as the valgrind detect, there is a "Invalid read"  

root@Starry:~/fuzz/ansilove# valgrind ./ansilove -i poc.ans  
==30030== Memcheck, a memory error detector  
==30030== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.  
==30030== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info  
==30030== Command: ./ansilove -i poc.ans  
==30030==  
AnsiLove/C 3.0.9 - ANSI / ASCII art to PNG converter  
Copyright (c) 2011-2018 Stefan Vogt, Brian Cassidy, and Frederic Cambus.  
==30030== Invalid read of size 1  
==30030==    at 0x50F9570: __strcmp_sse2_unaligned (strcmp-sse2-unaligned.S:24)  
==30030==    by 0x4023C0: main (main.c:238)  
==30030==  Address 0x81a82b0 is 0 bytes inside a block of size 144 free'd  
==30030==    at 0x4C2EDEB: free (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)  
==30030==    by 0x4051E6: sauceReadFile (sauce.c:34)  
==30030==    by 0x4051E6: sauceReadFileName (sauce.c:22)  
==30030==    by 0x40236F: main (main.c:230)  
==30030==  Block was alloc'd at  
==30030==    at 0x4C2DB8F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)  
==30030==    by 0x405198: sauceReadFile (sauce.c:31)  
==30030==    by 0x405198: sauceReadFileName (sauce.c:22)  
==30030==    by 0x40236F: main (main.c:230)  
==30030==  
  
Input File: poc.ans  
Output File: poc.ans.png  
==30030== Conditional jump or move depends on uninitialised value(s)  
==30030==    at 0x4E3D5B4: ansilove_ansi (in /usr/local/lib/libansilove.so.1.0.0)  
==30030==    by 0x4038A2: main (main.c:304)  
==30030==  
==30030== Invalid read of size 1  
==30030==    at 0x5095454: ____strtol_l_internal (strtol_l.c:293)  
==30030==    by 0x405D0F: strtonum (strtonum.c:50)  
==30030==    by 0x4E3D481: ansilove_ansi (in /usr/local/lib/libansilove.so.1.0.0)  
==30030==    by 0x4038A2: main (main.c:304)  
==30030==  Address 0x0 is not stack'd, malloc'd or (recently) free'd  
==30030==  
==30030==  
==30030== Process terminating with default action of signal 11 (SIGSEGV): dumping core  
==30030==  Access not within mapped region at address 0x0  
==30030==    at 0x5095454: ____strtol_l_internal (strtol_l.c:293)  
==30030==    by 0x405D0F: strtonum (strtonum.c:50)  
==30030==    by 0x4E3D481: ansilove_ansi (in /usr/local/lib/libansilove.so.1.0.0)  
==30030==    by 0x4038A2: main (main.c:304)  
==30030==  If you believe this happened as a result of a stack  
==30030==  overflow in your program's main thread (unlikely but  
==30030==  possible), you can try to increase the size of the  
==30030==  main thread stack using the --main-stacksize= flag.  
==30030==  The main thread stack size used in this run was 8388608.  
==30030==  
==30030== HEAP SUMMARY:  
==30030==     in use at exit: 3,361 bytes in 4 blocks  
==30030==   total heap usage: 232 allocs, 228 frees, 285,685 bytes allocated  
==30030==  
==30030== LEAK SUMMARY:  
==30030==    definitely lost: 0 bytes in 0 blocks  
==30030==    indirectly lost: 0 bytes in 0 blocks  
==30030==      possibly lost: 0 bytes in 0 blocks  
==30030==    still reachable: 3,361 bytes in 4 blocks  
==30030==         suppressed: 0 bytes in 0 blocks  
==30030== Rerun with --leak-check=full to see details of leaked memory  
==30030==  
==30030== For counts of detected and suppressed errors, rerun with: -v  
==30030== Use --track-origins=yes to see where uninitialised values come from  
==30030== ERROR SUMMARY: 169 errors from 3 contexts (suppressed: 0 from 0)  
Segmentation fault