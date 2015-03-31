C++ MISC Syntax
======

##### String API

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

##### C++ Array

```cpp
int A[5];       //fine
const int N = 5;
int B[N];       //fine
int M;
cin >> M;
int C[M];       //Illegal, some compilers accept it
```

######Remarks:
Must state max size up front and must be a compile-time constant


###### Vector API

```#include <vector>```

Syntax          | Use
----------------|------------------------
s.at(i)         | Returns ith element (checked access)
s[i]            | Returns ith element (unchecked access)
v.size()        | Returns # of elements
v.capacity()    | Returns # of elements of space
v.empty()       | Returns true iff v is emtpy
v.push_back(...)| Add element to end of v
v.pop_back(...) | Remove last elemetn from end
v.front()       | Returns reference to first element
v. begin()      | Returns iterator pointing to first element
v.end()         | Returns iterator pointing to last element
v.back()        | Returns reference to last element
v.resize(int)   | Reset size to exactly n, deleting/padding as needed
v.reserve(int)  |Reset capacity to max

###### Remarks
- ```v.size() <= v.capacity()```
- ```A[12]``` faster than ```A.at(12)``` due to no bounds checking
- Typical Uses: 
    - ```vector<string> monthName (12);```
    - ```monthName[0] = "January";```
    - ```vector<int> grades;```
    - ```grades.push_back(88);```

##### Command Line Arguments
```cpp 
int main(int argc, char* argv[]){}
```
- ```argc``` counts # of command-line args passed to the executable for that run
    - ```argv[0]``` holds name of command used to call program
- ```argv``` array of char*, one for each arg passed in for that run
