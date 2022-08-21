**Include guards**: <br/>
In the C and C++ programming languages, an **include guard**, sometimes called a **macro guard**, **header guard** or **file guard**, is a particular construct used to avoid the problem of double inclusion when dealing with the include directive. If certain C or C++ language constructs are defined twice, the resulting translation unit (a kind of copy of your source file) is invalid. **Include guards** prevent this erroneous construct from arising. 
<br/>

***Double inclusion example***:
> The following C code demonstrates a real problem that can arise if include guards are missing:

*File "grandparent.h"*
```c
struct foo {
    int member;
};
```

*File "parent.h"*
```header
#include "grandparent.h"
```

*File "child.c"*
```header
#include "grandparent.h"
#include "parent.h"
```

*Result*
```c
struct foo {
    int member;
};
struct foo {
    int member;
};
```
> Here, the file "child.c" has indirectly included two copies of the text in the header file "grandparent.h". This causes a compilation error, since the structure type foo will thus be defined twice.

In order to prevent this, we can add include guards in the **'.h'** file as follows:

*File "parent.h"*
```c
#ifndef GRANDPARENT_H
    #define GRANDPARENT_H

struct foo {
    int member;
};

#endif /* GRANDPARENT_H */
```
Here, the first inclusion of "grandparent.h" has the macro *GRANDPARENT_H* defined. When "child.c" includes "grandparent.h" at the second time, as the ```#ifndef``` test returns false, the preprocessor skips down to the ```#endif```, thus avoiding the second definition of ```struct foo```.

---

Source:
[Wikipedia](https://en.wikipedia.org/wiki/Include_guard)