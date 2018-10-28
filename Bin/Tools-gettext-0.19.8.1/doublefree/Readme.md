when run msgfmt to check a crafted file, an error was detected by the os.


ubuntu@VM-12-40-ubuntu:~/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src$ ./msgfmt --check ../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.\(nil\).INSTR.mov____0x10\(%rcx\)\,%r8.fuzz
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:17: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:16: ...this is the location of the first definition
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:18:3: syntax error
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:18: keyword "n" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:19: end-of-line within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:28: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:24: ...this is the location of the first definition
*** Error in `/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt': double free or corruption (fasttop): 0x000000000103de90 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7f47e5c317e5]
/lib/x86_64-linux-gnu/libc.so.6(+0x8037a)[0x7f47e5c3a37a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7f47e5c3e53c]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so(po_callback_comment_dispatcher+0x38c)[0x7f47e6293b8c]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so(po_gram_parse+0x137e)[0x7f47e629672e]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so(+0x104f7)[0x7f47e62974f7]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so(catalog_reader_parse+0x56)[0x7f47e6293026]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt[0x404ccf]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt[0x403e20]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f47e5bda830]
/home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt[0x404969]
======= Memory map: ========
00400000-00412000 r-xp 00000000 fd:01 1445529                            /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt
00611000-00612000 r--p 00011000 fd:01 1445529                            /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt
00612000-00613000 rw-p 00012000 fd:01 1445529                            /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/lt-msgfmt
01031000-01052000 rw-p 00000000 00:00 0                                  [heap]
7f47e0000000-7f47e0021000 rw-p 00000000 00:00 0
7f47e0021000-7f47e4000000 ---p 00000000 00:00 0
7f47e4909000-7f47e491f000 r-xp 00000000 fd:01 410135                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f47e491f000-7f47e4b1e000 ---p 00016000 fd:01 410135                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f47e4b1e000-7f47e4b1f000 rw-p 00015000 fd:01 410135                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f47e4b1f000-7f47e4b21000 r-xp 00000000 fd:01 216190                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f47e4b21000-7f47e4d20000 ---p 00002000 fd:01 216190                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f47e4d20000-7f47e4d21000 r--p 00001000 fd:01 216190                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f47e4d21000-7f47e4d22000 rw-p 00002000 fd:01 216190                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f47e4d22000-7f47e4f02000 r--p 00000000 fd:01 216565                     /usr/lib/locale/locale-archive
7f47e4f02000-7f47e500a000 r-xp 00000000 fd:01 412324                     /lib/x86_64-linux-gnu/libm-2.23.so
7f47e500a000-7f47e5209000 ---p 00108000 fd:01 412324                     /lib/x86_64-linux-gnu/libm-2.23.so
7f47e5209000-7f47e520a000 r--p 00107000 fd:01 412324                     /lib/x86_64-linux-gnu/libm-2.23.so
7f47e520a000-7f47e520b000 rw-p 00108000 fd:01 412324                     /lib/x86_64-linux-gnu/libm-2.23.so
7f47e520b000-7f47e520e000 r-xp 00000000 fd:01 412330                     /lib/x86_64-linux-gnu/libdl-2.23.so
7f47e520e000-7f47e540d000 ---p 00003000 fd:01 412330                     /lib/x86_64-linux-gnu/libdl-2.23.so
7f47e540d000-7f47e540e000 r--p 00002000 fd:01 412330                     /lib/x86_64-linux-gnu/libdl-2.23.so
7f47e540e000-7f47e540f000 rw-p 00003000 fd:01 412330                     /lib/x86_64-linux-gnu/libdl-2.23.so
7f47e540f000-7f47e5434000 r-xp 00000000 fd:01 410220                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f47e5434000-7f47e5633000 ---p 00025000 fd:01 410220                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f47e5633000-7f47e5637000 r--p 00024000 fd:01 410220                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f47e5637000-7f47e5638000 rw-p 00028000 fd:01 410220                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f47e5638000-7f47e5792000 r-xp 00000000 fd:01 222447                     /usr/local/lib/libxml2.so.2.9.7
7f47e5792000-7f47e5992000 ---p 0015a000 fd:01 222447                     /usr/local/lib/libxml2.so.2.9.7
7f47e5992000-7f47e599a000 r--p 0015a000 fd:01 222447                     /usr/local/lib/libxml2.so.2.9.7
7f47e599a000-7f47e599c000 rw-p 00162000 fd:01 222447                     /usr/local/lib/libxml2.so.2.9.7
7f47e599c000-7f47e599d000 rw-p 00000000 00:00 0
7f47e599d000-7f47e59b5000 r-xp 00000000 fd:01 412327                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7f47e59b5000-7f47e5bb4000 ---p 00018000 fd:01 412327                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7f47e5bb4000-7f47e5bb5000 r--p 00017000 fd:01 412327                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7f47e5bb5000-7f47e5bb6000 rw-p 00018000 fd:01 412327                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7f47e5bb6000-7f47e5bba000 rw-p 00000000 00:00 0
7f47e5bba000-7f47e5d7a000 r-xp 00000000 fd:01 412328                     /lib/x86_64-linux-gnu/libc-2.23.so
7f47e5d7a000-7f47e5f7a000 ---p 001c0000 fd:01 412328                     /lib/x86_64-linux-gnu/libc-2.23.so
7f47e5f7a000-7f47e5f7e000 r--p 001c0000 fd:01 412328                     /lib/x86_64-linux-gnu/libc-2.23.so
7f47e5f7e000-7f47e5f80000 rw-p 001c4000 fd:01 412328                     /lib/x86_64-linux-gnu/libc-2.23.so
7f47e5f80000-7f47e5f84000 rw-p 00000000 00:00 0
7f47e5f84000-7f47e607e000 r-xp 00000000 fd:01 1437329                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/gnulib-lib/.libs/libgettextlib-0.19.8.1.so
7f47e607e000-7f47e627d000 ---p 000fa000 fd:01 1437329                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/gnulib-lib/.libs/libgettextlib-0.19.8.1.so
7f47e627d000-7f47e627f000 r--p 000f9000 fd:01 1437329                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/gnulib-lib/.libs/libgettextlib-0.19.8.1.so
7f47e627f000-7f47e6283000 rw-p 000fb000 fd:01 1437329                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/gnulib-lib/.libs/libgettextlib-0.19.8.1.so
7f47e6283000-7f47e6287000 rw-p 00000000 00:00 0
7f47e6287000-7f47e62d3000 r-xp 00000000 fd:01 1445458                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so
7f47e62d3000-7f47e64d2000 ---p 0004c000 fd:01 1445458                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so
7f47e64d2000-7f47e64d3000 r--p 0004b000 fd:01 1445458                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so
7f47e64d3000-7f47e64d5000 rw-p 0004c000 fd:01 1445458                    /home/ubuntu/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src/.libs/libgettextsrc-0.19.8.1.so
7f47e64d5000-7f47e64fb000 r-xp 00000000 fd:01 412326                     /lib/x86_64-linux-gnu/ld-2.23.so
7f47e66d7000-7f47e66dd000 rw-p 00000000 00:00 0
7f47e66f1000-7f47e66f2000 rw-p 00000000 00:00 0
7f47e66f2000-7f47e66f9000 r--s 00000000 fd:01 216204                     /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7f47e66f9000-7f47e66fa000 rw-p 00000000 00:00 0
7f47e66fa000-7f47e66fb000 r--p 00025000 fd:01 412326                     /lib/x86_64-linux-gnu/ld-2.23.so
7f47e66fb000-7f47e66fc000 rw-p 00026000 fd:01 412326                     /lib/x86_64-linux-gnu/ld-2.23.so
7f47e66fc000-7f47e66fd000 rw-p 00000000 00:00 0
7ffc2b760000-7ffc2b782000 rw-p 00000000 00:00 0                          [stack]
7ffc2b7c7000-7ffc2b7ca000 r--p 00000000 00:00 0                          [vvar]
7ffc2b7ca000-7ffc2b7cc000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted


and the valgrind said:

==6238== Memcheck, a memory error detector
==6238== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.
==6238== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==6238== Command: .libs/lt-msgfmt --check ../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz
==6238==
==6238== Conditional jump or move depends on uninitialised value(s)
==6238==    at 0x50AC98C: freea (malloca.c:125)
==6238==    by 0x4E4A229: po_lex_charset_set (po-charset.c:632)
==6238==    by 0x4E499CC: do_callback_message (po-gram-gen.y:106)
==6238==    by 0x4E499CC: po_gram_parse (po-gram-gen.y:204)
==6238==    by 0x4E4A4F6: po_parse (read-po.c:41)
==6238==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==6238==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==6238==    by 0x403E1F: main (msgfmt.c:746)
==6238==
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:17: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:16: ...this is the location of the first definition
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:18:3: syntax error
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:18: keyword "n" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:19: end-of-line within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:28: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:24: ...this is the location of the first definition
==6238== Invalid free() / delete / delete[] / realloc()
==6238==    at 0x4C2EDEB: free (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==6238==    by 0x4E49599: po_gram_parse (po-gram-gen.y:237)
==6238==    by 0x4E4A4F6: po_parse (read-po.c:41)
==6238==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==6238==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==6238==    by 0x403E1F: main (msgfmt.c:746)
==6238==  Address 0x641f8b0 is 0 bytes inside a block of size 24 free'd
==6238==    at 0x4C2EDEB: free (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==6238==    by 0x4E4D8CE: default_add_message (read-catalog.c:378)
==6238==    by 0x4E4D583: call_add_message (read-catalog.c:64)
==6238==    by 0x4E4D583: default_directive_message (read-catalog.c:248)
==6238==    by 0x4E46139: call_directive_message (read-catalog-abstract.c:107)
==6238==    by 0x4E46139: po_callback_message (read-catalog-abstract.c:219)
==6238==    by 0x4E49935: do_callback_message (po-gram-gen.y:108)
==6238==    by 0x4E49935: po_gram_parse (po-gram-gen.y:225)
==6238==    by 0x4E4A4F6: po_parse (read-po.c:41)
==6238==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==6238==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==6238==    by 0x403E1F: main (msgfmt.c:746)
==6238==  Block was alloc'd at
==6238==    at 0x4C2DB8F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==6238==    by 0x50BC3D8: xmalloc (xmalloc.c:65)
==6238==    by 0x50BC4F1: xstrdup (xstrdup.c:40)
==6238==    by 0x4E4CE7F: string_list_append (str-list.c:74)
==6238==    by 0x4E48A3E: po_gram_parse (po-gram-gen.y:417)
==6238==    by 0x4E4A4F6: po_parse (read-po.c:41)
==6238==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==6238==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==6238==    by 0x403E1F: main (msgfmt.c:746)
==6238==
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:35: keyword "msgud_plural" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:34: missing 'msgstr' section
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:35:13: syntax error
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:40: end-of-line within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:46: end-of-line within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz: warning: Charset missing in header.
                                                                                                                                                                   Message conversion to user's charset will not work.
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:42: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:6: ...this is the location of the first definition
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:46:2: syntax error
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:46: keyword "Ep" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:47: keyword "C" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:48: keyword "s" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:49: keyword "bo" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:50: keyword "S" unknown
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:50:236: invalid control sequence
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:50:397: invalid control sequence
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.7ffff672fbed.STACK.19a5afbc2a.CODE.128.ADDR.(nil).INSTR.mov____0x10(%rcx),%r8.fuzz:51: end-of-line within string
.libs/lt-msgfmt: too many errors, aborting
==6238==
==6238== HEAP SUMMARY:
==6238==     in use at exit: 41,477 bytes in 117 blocks
==6238==   total heap usage: 635 allocs, 519 frees, 86,604 bytes allocated
==6238==
==6238== LEAK SUMMARY:
==6238==    definitely lost: 650 bytes in 82 blocks
==6238==    indirectly lost: 0 bytes in 0 blocks
==6238==      possibly lost: 0 bytes in 0 blocks
==6238==    still reachable: 40,827 bytes in 35 blocks
==6238==         suppressed: 0 bytes in 0 blocks
==6238== Rerun with --leak-check=full to see details of leaked memory
==6238==
==6238== For counts of detected and suppressed errors, rerun with: -v
==6238== Use --track-origins=yes to see where uninitialised values come from
==6238== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 0 from 0)

