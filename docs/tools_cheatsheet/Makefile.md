**A simple Makefile**

```Makefile
    CC  =	gcc

    NAME  =	binary_name

    CFLAGS  =	 -Wpedantic -pedantic-errors -w  -Wextra  -Wall -Iinclude

    SRC = core/my_printf.c \
        core/save_printf.c \
	    src/my_putstr.c	   \
	    src/my_putchar.c   \
    	src/my_strlen.c	   \
        main.c

    OBJ	=	$(SRC:.c=.o)

    all:  $(NAME)

    $(NAME):	$(OBJ)
	    $(CC) -c $(OBJ) -o $(NAME)

    clean:
	    -rm -f $(OBJ)

    fclean:	clean
	    -rm -f $(NAME)

    re:	fclean all

    .PHONY:	fclean clean re
```

---

**Graphical Makefile Template**

In this template I have a folder named *src* where is located all our *.c* file except the *main.c* which is root located.
The *$(shell find src/ -name '*.c')* means to Makefile to find all the *.c* files which are located in the folder *src* including all the sub directory inside it.

```Makefile
    CC	=	gcc

    CSFML	+=	-lcsfml-graphics -lcsfml-window -lcsfml-audio -lcsfml-system

    CFLAGS	+=	-Wpedantic -pedantic-errors -w  -Wextra  -Wall $(CSFML) -Iinc

    NAME	=	name_of_the_binary

    SRC	=	$(shell find src/ -name '*.c')\
		  main.c

    OBJ	=	$(SRC:.c=.o)

    all:	$(NAME)

    $(NAME):	$(OBJ)
	    $(CC) $(CFLAGS) $(OBJ) $(LIB) -o $(NAME) 
	    rm -f $(OBJ) *~

    clean:
	    rm -f src/*.o
	    rm -f *~ core/*~ inc/*~ src/*~

    fclean: clean
	    rm -f $(NAME)
	    rm -f a.out src/a.out core/a.out a.out

    re:	fclean all

    .PHONY:	fclean	clean	re
```
Some useful flags and possibilities of customs makefile you can use

---

## How make processes a Makefile

By default, makes start with the first target. It reads the Makefile<br/>
in the current directory and begins by processing the first rule. A <br/>
rule appears in the makefile and says when and how to remake certain<br/>
files, called the rule's ```targets``` (most often only one per rule).<br/>
The general syntax for a rule is:

```Makefile
target: [ prerequisites ]
    [ command ]
```
```A target``` is usually the name of a file that is generated by a program. It can also be the name of an action to carry out, such as re, fclean.<br/>
```A prerequisite``` is a file that is used as input to create the target.

## Clean rule

Beside compiling a program, a Makefile can help you with cleaning the unnecessary files in your directory such as .o, .gcno, .gcda, .gcovr. We can write a ```clean``` rule to help us as follows:

```Makefile
clean:
    rm -f *.o
    rm -f *.gcda
    rm -f *.gcno
    rm -f *.gcovr
```
To prevent make from getting confused by a file called "clean" and force it to stop when an error occurs, we might want to rewrite the rule:

```Makefile
.PHONY : clean
clean : 
    rm -f *.o
    rm -f *.gcda
    rm -f *.gcno
    rm -f *.gcovr
```
There are two reasons to use a phony target: to avoid a conflict with a file of the same name, and to improve performance. 

## Adding unit_tests rule

It is considered as a good practice (pattern) to implement the unit tests for all your functions. We'll see here how you can create a rule for your unit tests inside your Makefile.

***Unit tests rule***

```Makefile
tests_run: $(TEST_SRC)
    gcc $(TEST_SRC) -o $(TEST_NAME) --coverage -lcriterion
    ./$(TEST_NAME)
    gcovr --exclude tests/
    gcovr --exclude tests/ --branches
```
Let's understand what happened here.

```The first line``` help us to compile the sources files with criterion.<br/>
Criterion add it's own main so none of the files we are compiling <br/>
should contain a main function. ```The second one``` execute the generated<br/>
binary. The execution of your unit-tests binary should create a bunch<br/>
of ```.gcda``` and ```.gcno``` files. These can be used by tools such as gcovr<br/>
to calculate the amount of code executed by your test. To calculate the number<br/>
of lines executed by your test, we can use the ```third command```<br/>
```The fourth command``` does the same thing, but with branches.

<u>Sources: <br/></u>
[MIT OPEN COURSEWAR](https://ocw.mit.edu/courses/1-124j-foundations-of-software-engineering-fall-2000/pages/lecture-notes/gnu_makefile_documentation/)<br/>
[DEV TO](https://dev.to/iamkhalil42/all-you-need-to-know-about-c-static-libraries-1o0b)