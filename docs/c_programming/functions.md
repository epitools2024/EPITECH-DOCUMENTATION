![Logo of C](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRvSKZqs76ra9ZzvgCR51vCoFGA2HLQH3EvFg&usqp=CAU)

**_Welcome to the necessary functions section in C for a student from Epitech._**

As the title indicates, in this section we will especially talk about some necessary functions in C for a student from Epitech.

Let's go !!!

---

_**1. Hello World**_

If you don't know it, it has become a **tradition** in the developer culture to start learning a new language by writing a function displaying the message "Hello World".

[More ...](helloworld_knowmore.md)

```c
int main(int ac, char **av)
{
    int fd = 1; // fd is the file descriptor (see man page of write)
    int n = 12; // n is the number of characters of the string to print

    write(fd, "Hello World\n", n);
    return (0);
}
```
---

**2. my_putchar**

my_putchar is one of the first functions to be coded in C at Epitech. It takes a single parameter, a character, which it then displays on the standard output.

 -[x] **Prototype** : ``` void my_putchar(char c);```

 -[x] **Output** : The character passed as a parameter.

 -[x] **Return** : _Anything_

---

**3. my_strlen**

my_strlen is a function that counts and returns the number of characters found in the string passed as parameter.

 -[x] **Prototype** : ``` int my_strlen(char const *str);```

 -[x] **Output** : Nothing on the standard output.
 
 -[x] **Return** : A int that represents number of characters found in the string passed as parameter.


---

**4. my_putstr**

my_putstr is  a function that displays, one-by-one, the characters of a string.
The address of the string’s first character will be found in the pointer passed as a parameter to the function.

 -[x] **Prototype** : 
 
 ``` void my_putstr(char const *str);```
 
 OR
 
 ``` int my_putstr (char const *str);```

 -[x] **Output** : Display the string passed as a parameter.
 
 -[x] **Return** : _Anything_ in the first case and O or 1 in the second case. 

---

**5. my_putnbr**

my_putnbr is a function that displays a number ( a int ) passed as a parameter.

 -[x] **Prototype** : ``` int my_put_nbr(int nb);```

 -[x] **Output** : Display the number passed as a parameter.
 
 -[x] **Return** : O or 1 by default.
 
---

**6. my_getnbr**

my_getnbr is a function that returns a number, sent as a string.

 -[x] **Prototype** : ``` int my_getnbr(char const *str);```

 -[x] **Output** : _Anything_.
 
 -[x] **Return** : Return a number sent as a string.
 
---

**7. my_strcpy**

my_strcpy is a function that copies a string into another. The destination string will already have enough memory to copy the source string.

 -[x] **Prototype** : ``` char *my_strcpy(char *dest, char const *src);```

 -[x] **Output** : _Anything_.

 -[x] **Return** : The string.
 
---

**8. my_strcmp**

my_strcmp is a function that compares two strings character by character.

 -[x] **Prototype** : ``` int my_strcmp(char const *s1, char const *s2);```

 -[x] **Output** : _Anything_.

 -[x] **Return** : 0 if both strings are the same else 1.
 
---

**9. my_strcat**

my_strcat is a function that concatenates two strings passed as parameters.

 -[x] **Prototype** : ``` char *my_strcat(char *dest, char const *src);```

 -[x] **Output** : _Anything_.

 -[x] **Return** : The chain resulting from the concatenation.
 
---

**10. my_str_to_word_array**

my_str_to_word_array is a function that splits a string into words arranged in order in a double table.

 -[x] **Prototype** : ``` char **my_str_to_word_array(char const *str);```

 -[x] **Output** : _Anything_.

 -[x] **Return** : The double table with the strings resulting from the parsing of the chain.

---