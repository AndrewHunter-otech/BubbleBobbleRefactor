# Bubble Bobble Refactored Design

## Screens Architecture

The `App` class handles the current state of the entire program and handles
updating and drawing screens. One `App` object is created globally which
has an update and draw method that are called from the *required* global update
and call functions.

State management is handled by instances of the `Screen` class. Each different
state is a child of `Screen` and they are:

1. `MenuScreen` Startup state. Handles showing the main menu and starting the game
2. `PlayScreen` Handles running and ending the game
3. `GameOverScreen` Handles showing the game over screen and going back to the
main menu

Each screen has an update and draw method which are called by app. As well they
can call `app.change_screen` to switch the games state to a different screen.

## Input Design

Input is handled by the `InputState` class. One instance of `InputState` is created
and stored in `App` each input action is a boolean field of `InputState`.

They are:
- `jump_pressed`
- `fire_pressed`
- `pause_pressed`
- `left`
- `right`
- `jump_held`
- `fire_held`
- `pause_held`

Actions are followed by pressed if the action is only active on the first frame
the key is pressed.

So to get if fire was pressed you simply check `input_state.fire_pressed`.

Each frame app calls update on its input state to populate its fields with
new values from the global keyboard object.

## Pausing

Pausing is implemented as a simple boolean field of the `PlayScreen`. In its
update method it checks if pause was just pressed and if so it flips the state
of its pause field. In update if the game is paused the state of the global `Game`
object is not updated but it is still drawn. Additionally the text PAUSED is drawn
in the middle of the screen.
