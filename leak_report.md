# Leak report

Valgrind reports that 46 bytes were definitely lost. They were allocated by calloc which was called on line 41 of check_whitespace.c in the function strip. The function strip is being called on line 62 of of check_whitespace.c in the function is_clean. Then is_clean is being called in main on line 87 of check_whitespace.c

