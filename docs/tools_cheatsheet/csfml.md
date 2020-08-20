# How to understand and start 2D game :robot:

## *Understand the game*

A 2D game is mainly a kind of program which generally follow a guideline.
It is made with 3 main parts:

- *Initialization*
- *Game loop*
- *Free resources*

You notice the game core is the game loop.
But we will describe the two others parts.

- ***Initialization***

    In this part you load in memory all the component you want to use inside your game loop.
    You have to initialize the variables you want to use with the right element, sprite, sound, image, text, all your asset and whatever you want to use inside the game.
    It is also here you will fix the position of your assets (for example you will set the positions of all the assets, probably decide if you want to play the main sound of your game as soon as the game start).
    It is important to do this part before the game loop.

---

- ***Game loop***

    The game loop is the main part of the game. It is here you will implement the game logic, manage events and also where you will draw the assets.
    By game logic, I mean all the game "itself". It is here you will define how the player will move, how the score will be displayed, what will happen if the player clicks on "Play" button, etc...
    It is here where you will define whatever should happen according to events. An event could be a keyboard input, collision between two objects, when a click happens and others such things.
    So the game loop is divided in three parts:

  - event loop : where you manage all the events which will happen in the game ,

  - update : where live the game logic,

  - drawing : the part where you draw all the asset you want in the game.

    You could follow this way to correctly setup or organize your future game project.

---

- ***Free resources***

  In this part you free (if necessary.. because it depends on your programming language) the all the memory you should have used in your game

---

:smirk:
This just an overview of the organization of a video game project. It may change depend on the game engine and barely of the framework you use.
So feel free to follow the way you want to follow

## *Set up the game in CSFML*

### Basics

Let go to a new step. You wanna create a game. Let make first a simple window.

```c
  #include <SFML/Graphics.h>
  #include <SFML/Config.h>
  #include <SFML/Audio.h>
  #include <SFML/System.h>

  sfRenderWindow *create_window(unsigned int width, unsigned int height, char const *title)
  {
    sfRenderWindow *Window;
    sfVideoMode mode;

    mode.width = width;
    mode.height = height;
    mode.bitsPerPixel = 32;
    Window = sfRenderWindow_create(mode, title, sfResize | sfClose, NULL);
    return (Window);
  }

  int main()
  {
    sfRenderWindow *window = create_window(800, 600, "CSFML");
    sfEvent event;
    while (sfRenderWindow_isOpen(window)) {
       sfRenderWindow_clear(window, sfBlack);
        while (sfRenderWindow_pollEvent(window, &event)) {
            if (event.type == sfEvtClosed || sfKeyboard_isKeyPressed(sfKeyEscape))
                sfRenderWindow_close(window);
        }
      sfRenderWindow_display(window);
    }
    sfRenderWindow_destroy(window);
  }
  
```

Put this code inside a file, ``file_name.c``.
You can compile this code with `gcc file_name.c -lcsfml-graphics -lcsfml-window`. If you launched it, you will see a black window. Simple and basic.

### Explanation

Let explain this pretty code you've compiled.

```c
  #include <SFML/Graphics.h>
  #include <SFML/Config.h>
  #include <SFML/Audio.h>
  #include <SFML/System.h>
```

Those lines refer to the main include you will use for all your Epitech game project. It contains all you need for graphic, sound, manage user key input, etc....

```c
sfRenderWindow *create_window(unsigned int width,
                              unsigned int height, char const *title)
  {
    sfRenderWindow *Window;
    sfVideoMode mode;

    mode.width = width;
    mode.height = height;
    mode.bitsPerPixel = 32;
    Window = sfRenderWindow_create(mode, title, sfResize | sfClose, NULL);
    return (Window);
  }
```

This function will be very useful through all the MUL projects you will build this year. It take in parameters the width, the height and the title of the screen. Inside, ``sfRenderWindow *Window`` refers to the window where all the game will be played, ``sfVideoMode mode`` refers to the screen's configuration (the width, the height and the number of bits per pixel which impact the global window's resolution).

```c
    sfRenderWindow *window = create_window(800, 600, "CSFML");
    sfEvent event;
```

I guess you can understand that... Don't be stupid :smirk:!

```c
  while (sfRenderWindow_isOpen(window))
```

This is the main loop of the game, which run while window is not closed. It can be replace also by ``while(running)`` with running a boolean value set to *true*. Close the window is so the same as set ``running`` to *false*.

```c
sfRenderWindow_clear(window, sfBlack);
```

This line allows screen to refresh every time all the actions you declare in the game loop ended. It make sure you will not have an error in your displaying. It also provide a way to set a custom background color.

```c
while (sfRenderWindow_pollEvent(window, &event))
```

It this loop, you will be able to handle every event which should happens at least one time such collision, user input and may other things.

```c
if (event.type == sfEvtClosed || sfKeyboard_isKeyPressed(sfKeyEscape))
                sfRenderWindow_close(window);
```

This condition is just : "*If the event which happens is sfEvtClosed (if the user want to close the window by clicking on the red cross button on the top of your window), close the game's render window.*"

```c
sfRenderWindow_display(window);
```

This line allows you to continue to display the game's window as the game is going on.

```c
sfRenderWindow_destroy(window);
```

This line free the resources allocated to display the window. It is a **VERY IMPORTANT STEP**. It makes your program more stable and able to run with much amount of variables and data.

## *How to use correctly the documentation*

There is no tutorials about CSFML on internet.
The only one you will find is an portuguese video tutorial about it. But it still a few useless when you look at the amount of work you will have to achieve.
The right way to use the documentation... That is a great deal to handle this year in graphical programming... 5 credits for the first semester and 9 for the second one. So I will give you some tips about it.
The first thing you have to handle is the logic of the documentation. All the ``.h`` files located in the ***File***  tab. If you're looking for some functions about audio management, you have to search the `Audio.h` file documentation. And if you need something about sprite handling: `Sprite.h`, about keyboard management: `Keyboard.h`.
By doing this you'll be able to easily find your way through this documentation.
Other tips: **Take time to read it**. It is not difficult. And if you take time just to understand the way everything is going on through this docs, you'll easily be able to understand a lot about 2D game's logic.

## *More tips and help*

If you want more tricks about CSFML... Don't hesitate to visit [CleanSFML](https://github.com/NemesisX1/CleanSFML) project.
