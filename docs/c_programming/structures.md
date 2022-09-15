In C programming, structures (also called structs) are a way to group several ***related variables*** into one place.<br/>
Each variable in the structure is known as a ```member``` of the structure. Unlike an array, a structure can contain many different data types. The different variables can be accessed via a ***single pointer*** or by ***the struct declared name*** which returns the same address.

<u>***Declare a Structure:***</u><br/>
The general syntax for a struct declaration in C is:
```c
struct name {
    type member1;
    type member2;
};
```
<br/>

<u>***Initialize a structure:***</u><br/>
Let's assume that we have a structure named ```player``` declared as follow:
```C
struct player {
    unsigned int height;
    unsigned int width;
    unsigned int health_point;
};
```

You can:

.Define a variable ```p1``` of type ```player``` and initialize its members according to the declaration order in the structure as follow:
```C
    struct player p1 = {800, 600, 1200}; 
                /* OR */
    struct player p1 = (struct player){800, 600, 1200};
```
<br/>
.Use designated initializer style to access each member in a random order:
```C
    struct player p1 = {.health_point = 1200, .width = 600, .height = 800};
```
<br/>
***Note: If an initializer is given or if the object is ```statically``` allocated, omitted elements are initialized to 0***.

.Copy the value of an existing object of the same type:
```C
    struct player p2 = p1; /* p2 will share the same properties as p1 */
```

Source:<br/>
[Wikipedia](https://en.wikipedia.org/wiki/Struct_(C_programming_language))

Best resources to study this topic:<br/>
[GeeksForGeeks](https://www.geeksforgeeks.org/structures-c/)<br/>
[OpenClassroom](https://openclassrooms.com/fr/courses/19980-apprenez-a-programmer-en-c/16119-creez-vos-propres-types-de-variables)<br/>
[C advanced doc - DevDocs](https://devdocs.io/c/language/struct)<br/>
