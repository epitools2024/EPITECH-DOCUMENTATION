**Parameterized macros**

One of the powerful functions of the C preprocessor is the ability to simulate functions using parameterized macros. For example, we might have some code to get the absolute value of an integer as follows:

```C
int abs(int number) 
{
    if (number < 0)
        return (number * (-1));
    return number;
}
```
<br/>
We can rewrite the above code using a macro as follows:

```header
#define ABS(x) (x < 0 ? -x : x)
```
<br/>
Macros with arguments must be defined using the ```#define``` directive before they can be used. The argument list is enclosed in parentheses and must immediately follow the macro name. Spaces are not allowed between the macro name and open parenthesis.

To learn about preprocessor operators:
[Tutorials Point](https://www.tutorialspoint.com/cprogramming/c_preprocessors.htm)
