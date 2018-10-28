as the valgrind report, there is a heap corruption

run: lt-msgfmt --check  poc

==21938== Memcheck, a memory error detector
==21938== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.
==21938== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==21938== Command: .libs/lt-msgfmt --check ../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz
==21938==
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:9: end-of-line within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz: warning: Charset missing in header.
                                                                                                                                                       Message conversion to user's charset will not work.
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:20: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:11: ...this is the location of the first definition
==21938== Invalid free() / delete / delete[] / realloc()
==21938==    at 0x4C2EDEB: free (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==21938==    by 0x4E49599: po_gram_parse (po-gram-gen.y:237)
==21938==    by 0x4E4A4F6: po_parse (read-po.c:41)
==21938==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==21938==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==21938==    by 0x403E1F: main (msgfmt.c:746)
==21938==  Address 0x6415bf0 is 0 bytes inside a block of size 21 free'd
==21938==    at 0x4C2EDEB: free (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==21938==    by 0x4E4D8CE: default_add_message (read-catalog.c:378)
==21938==    by 0x4E4D583: call_add_message (read-catalog.c:64)
==21938==    by 0x4E4D583: default_directive_message (read-catalog.c:248)
==21938==    by 0x4E46139: call_directive_message (read-catalog-abstract.c:107)
==21938==    by 0x4E46139: po_callback_message (read-catalog-abstract.c:219)
==21938==    by 0x4E49935: do_callback_message (po-gram-gen.y:108)
==21938==    by 0x4E49935: po_gram_parse (po-gram-gen.y:225)
==21938==    by 0x4E4A4F6: po_parse (read-po.c:41)
==21938==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==21938==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==21938==    by 0x403E1F: main (msgfmt.c:746)
==21938==  Block was alloc'd at
==21938==    at 0x4C2DB8F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==21938==    by 0x50BC3D8: xmalloc (xmalloc.c:65)
==21938==    by 0x50BC4F1: xstrdup (xstrdup.c:40)
==21938==    by 0x4E4CE7F: string_list_append (str-list.c:74)
==21938==    by 0x4E48A3E: po_gram_parse (po-gram-gen.y:417)
==21938==    by 0x4E4A4F6: po_parse (read-po.c:41)
==21938==    by 0x4E46025: catalog_reader_parse (read-catalog-abstract.c:179)
==21938==    by 0x404CCE: read_catalog_file_msgfmt (msgfmt.c:1415)
==21938==    by 0x403E1F: main (msgfmt.c:746)
==21938==
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:38: end-of-file within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:32: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:11: ...this is the location of the first definition
.libs/lt-msgfmt: found 4 fatal errors
==21938==
==21938== HEAP SUMMARY:
==21938==     in use at exit: 7,068 bytes in 24 blocks
==21938==   total heap usage: 187 allocs, 165 frees, 30,569 bytes allocated
==21938==
==21938== LEAK SUMMARY:
==21938==    definitely lost: 0 bytes in 0 blocks
==21938==    indirectly lost: 0 bytes in 0 blocks
==21938==      possibly lost: 0 bytes in 0 blocks
==21938==    still reachable: 7,068 bytes in 24 blocks
==21938==         suppressed: 0 bytes in 0 blocks
==21938== Rerun with --leak-check=full to see details of leaked memory
==21938==
==21938== For counts of detected and suppressed errors, rerun with: -v
==21938== ERROR SUMMARY: 2 errors from 1 contexts (suppressed: 0 from 0)
ubuntu@VM-12-40-ubuntu:~/fuzz/gettext-0.19.8.1-san/gettext-0.19.8.1/gettext-tools/src$ .libs/lt-msgfmt --check  ../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.\(nil\).INSTR.movzbl_\(%rax\)\,%edx.fuzz
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:9: end-of-line within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz: warning: Charset missing in header.
                                                                                                                                                       Message conversion to user's charset will not work.
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:20: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:11: ...this is the location of the first definition
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:38: end-of-file within string
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:32: duplicate message definition...
../../../../gettext-0.19.8.1/gettext-tools/src/fuzz_msgfmt/SIGSEGV.PC.444879.STACK.d256ac445.CODE.1.ADDR.(nil).INSTR.movzbl_(%rax),%edx.fuzz:11: ...this is the location of the first definition
Segmentation fault