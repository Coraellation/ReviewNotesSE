C++ MISC Syntax
======

#### String API

```#include <string>```

Syntax          | Use
----------------|------------------------
+               | Concatenation
==, <=, <,      | Comparison by ordering
s.length()      | Counts chars in s
s.substr(i,n)   | Substring n chars starting at i
s.substr(i)     | Substring starting at i to the end
s.at(i)         | Returns ith char (checked access)
s[i]            | Returns ith char (unchecked access)
s.c_str()       | Returns C-style char* equivalent of s
s.find(str,pos) | Returns first index of str in s starting at/after pos (else -1)
s.rfind(str, pos)| Returns last index of str in s starting at/before pos
s.replace(...)  | Replaces chars within s
s.insert(...)   | Insert chars within s
