# How to understand and start 2D game :robot:

## *Understand the game*

A 2D game is mainly a king of program which generally follow a guideline.
It is made with 3 main parts:

- *Initialization*
- *Game loop*
- *Free resources*

You notice the game core is the game loop.
But we will describe the two others parts.

- ***Initialization***

    In this part you load in the memory all the component you want to use inside your game loop.
    You have to initialize the variables you want to use with the right element, sprite, sound, image, text, all your asset and whatever you want to use inside the game.
    It is also here you will fix the position of your assets (for example you will set the positions of all the assets, probably decide if you want to play the main sound of your game as soon as the game start).
    It is important to do this part before the game loop.

---

- ***Game loop***

    The game loop is the main part of the game. It is here you will implement the game logic, manage events and also where you will draw the assets.
    By game logic, I mean all the game "itself". It is here you will define how the player will move, how the score will be displayed, what will happen if you click on "Play", etc...
    It is here where you will define whatever should happens according to the events. An event could be a keyboard input, the collision between two objects, check when a click happens and others things as it.
    So the game loop is divided in three parts:

  - event loop : where you manage all the events   which will happen in the game ,

  - update : where live the game logic ,

  - drawing : the part where you draw all the asset you want in the game.

    You could follow this way to correctly setup or organize your future game project.

---

- ***Free resources***

  It this part you free (is necessary because it depends on your programming language) the all the memory you should have used in your game

---

:smirk:
This just an overview of the organization of a video game project. It may change depend on the game engine and barely of the framework you use.
So feel free to follow the way you want to follow

## *Set up the game in CSFML*
Let go to a new step. You wanna create a game. Let make first a simple window.
```c
  #include <SFML/Graphics.h>
  #include <SFML/Config.h>
  #include <SFML/Audio.h>
  #include <SFML/System.h>

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

  int main() 
  {
    sfRenderWindow *window = create_window(800, 600, "CSFML");
    sfEvent event;
    while (sfRenderWindow_isOpen(window)) {
       sfRenderWindow_clear(window, sfBlack);
        while (sfRenderWindow_pollEvent(window, &event)) {
            if (event.type == sfEvtClosed
                || sfKeyboard_isKeyPressed(sfKeyEscape))
                sfRenderWindow_close(window);
        }
      sfRenderWindow_display(window);
    }
    sfRenderWindow_destroy(window);
  }
  
```
