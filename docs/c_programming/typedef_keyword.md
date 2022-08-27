The **typedef** is a keyword used in C programming to provide some meaningful names<br/>
to the already existing variables in the C program. It is used to create an additional name (alias) for another data type, but does not create a new type.

In short, we can say that this keyword is used to **redefine the name of an already existing variable**.

***Syntax***:<br/>
    ```
    typedef <data_type> <alias>;
    ```
<br/>

***Examples***:<br/>
    ```
    typedef unsigned int unit;
    ```
<br/>

In the above statements, we have replaced the *unsigned int* type by an alias named *unit* by using a typedef keyword.

Now, we can create the variables of type *unsigned int* by writing:<br/>
    ```
    unit a = 42;
    ```

As a student at EPITECH, you'll mostly use typedef with structures.
Consider the below structure declaration:<br/>

```c
struct student {
    int age;
    char *name;
    void *random_data;
}
```
<br/>
We have created a data of type **struct person**. But for each call of this type, we'll have to write<br/> 
```struct person s1``` and it can become tedious.
That's why we'll use ```typedef```:<br/>

```c
typedef struct student {
    int age;
    char *name;
    void *random_data;
}student_t;
```

From the above declaration, we notice that typedef keyword reduces the length of the code and complexity of data type. From now, we just have
to write ```student_t s1``` to create a variable s1 of type struct student.

For more information on the subject, we suggest the following link:<br/>
[C typedef](https://devdocs.io/c/language/typedef)