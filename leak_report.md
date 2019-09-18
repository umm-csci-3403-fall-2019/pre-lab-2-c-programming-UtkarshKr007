# Leak report

Valgrind reports that 46 bytes were definitely lost. They were allocated by calloc in the function strip on line 41 of check_whitespace.c. The function strip is being called on line 62 of of check_whitespace.c in the function
is_clean. Finally, is_clean is being called in main on line 87 of check_whitespace.c. The char* declared in function strip are being returned to is_clean, so they can't be freed there. The function is_clean however only uses
the char* for comparision and stores it result as a int before performing one more comparision and returning a boolean to main. To fix the memory leak, we can free varaible 'cleaned' in is_clean after the comparision using it has finished.
