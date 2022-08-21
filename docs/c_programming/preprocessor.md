The C Preprocessor is **not** a part of the compiler, but is a **separate step in the compilation process**. In simple terms, a C Preprocessor is just a text substitution tool and it instructs the compiler to **do required pre-processing before the actual compilation**. All preprocessor commands begin with a hash symbol (#).

***Preprocessor examples***:<br/>
Consider the following directives:<br/>
```header
#define ARRAY_LEN 42;
```
This directive tells the C preprocessor to replace instances of ARRAY_LEN with 42.

```header
#include <stdlib.h> 
```
The C preprocessor processes directives of the form ```#include <file>``` in a source file (.c file) by locating the associated file on disk and including its contents into a copy of the source file, replacing the include directive in the process.

```header
#ifndef HEADER_H
    #define HEADER_H
#endif
```
It tells the C preprocessor to define HEADER_H only if HEADER_H is not already defined. It is called *include guards*.

---

Source:
[Wikipedia](https://en.wikipedia.org/wiki/Include_guard)

_References_:<br/>
[C Documentation about preprocessor and directives](https://devdocs.io/c/preprocessor)