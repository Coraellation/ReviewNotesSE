Basics of Object-Oriented Programming
======

###Iterators

###### Overview

`foo(iter1, iter2)`

- Used to navigate through containers
- Given a **ptr** to the first element of the collection (c.begin(), p=iter1) 
- Given a ptr to **just beyond** the last element (stop when p==iter2, c.end())
- Dereferencing iterator/ptr gets to element (*p)
- Bi-directional iterators define both p++ (advance to next element) and p-- (moves backwards)

`Const Iterators`: Promise to not change anything in collection; cbegin()/cend() in C++11, begin()/end() otherwise
###### Const Iterator 
```cpp
#include <iostream>
#include <string>
#include <vector>
using namespace std;

int main(int argc, char* argv[]){
	vector<string> words;
	words.push_back("eggs");
	words.push_back("bacon");
	words.push_back("ham");

	for (vector<string>::const_iterator wordsIter = words.begin(); 
		wordsIter != words.end(); wordsIter++){
		cout << *wordsIter << endl;
	}
	return 0;
}
```

###### Reverse Iterator
```cpp
for (vector<string>::reverse_iterator rit = words.rbegin();
    rit != words.rend(); rit++){
    cout << *rit << endl;
}
```



`Random Access Iterators`: Allows access to randomd elements in no worse than **ACT**

- For vectors, if f is an iterator, f[3] is the third element after the element pointed to by f (does not support operator[])
- However, STL lists are not continguous memory and thus are not random access; must follow k pointeres to get to element desired (does not support operator[])
- Similarly, STL maps are implemented as red-black trees, and thus cannot jump to third element (does not support operator[])