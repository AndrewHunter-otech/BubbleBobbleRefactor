# Bubble Bobble Refactored
#### Andrew Hunter 100877101

## How to Run

1. Install python >= 3.5 pygame and pgzero >= 1.2
2. Run `python cavern.py`
3. Arrow keys to move, space to shoot, p to pause
4. Enjoy

## Summary of Architectural Changes

- The old system of states handled with if statements in a global update and draw
function is replaced by a system of Screens for each state of the game handled
by and App object
- Input is handled by a InputState object which is passed when needed
- The game can be paused by pressing `p` while playing
