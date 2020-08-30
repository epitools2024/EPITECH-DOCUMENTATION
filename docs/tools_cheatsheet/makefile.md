**A simple Makefile**

```makefile
    CC	=	gcc

    NAME	=	name_of_binary

    CFLAGS	=	 -Wpedantic -pedantic-errors -w  -Wextra  -Wall -Iinclude

    SRC	=	core/my_printf.c \
	    	core/save_printf.c \
		src/my_putstr.c	\
	        src/my_putchar.c	\
    	        src/my_strlen.c	\
                main.c

    OBJ	=	$(SRC:.c=.o)

    all:	$(NAME)

    $(NAME):	$(OBJ)
	    $(CC) -c $(OBJ)
	    ar rc $(NAME) $(OBJ)

    clean:
	    rm -f $(OBJ)

    fclean:	clean
	    rm -f $(NAME)

    re:	fclean all

    .PHONY:	fclean clean re
```

---

**Graphical Makefile Template**

In this template I have a folder named *src* where is located all my *.c* file except the *main.c* which is root located.
The *$(shell find src/ -name '*.c')* means to Makefile to find all the *.c* files which are located in the folder *src* including all the sub directory inside it.

```makefile
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