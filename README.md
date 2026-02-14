# Player Interface Documentation

This document explains the logic and structure of the `player interface.py` script, which simulates a simple RPG character movement system.

## Overview
The script uses **Object-Oriented Programming (OOP)** to define a generic character template and a specific implementation. It relies on **Abstraction** to enforce structure and **Inheritance** to share logic.

## Class Breakdown

### 1. `Player` (Abstract Base Class)
The `Player` class is a blueprint. It inherits from `ABC` (Abstract Base Class) and cannot be instantiated directly.

- **`__init__(self)`**:
  - **What it does**: Sets up the initial state.
  - **Details**: Initializes `self.moves` (empty list), `self.position` (starts at `0,0`), and `self.path` (history of locations).

- **`make_move(self)`**:
  - **What it does**: Simulates taking a single step in a random direction.
  - **How?**:
    1. Selects a random tuple (e.g., `(0, 1)`) from `self.moves`.
    2. Adds this tuple to the current `self.position` to get new coordinates.
    3. Appends the new position to `self.path`.
    4. Updates `self.position` and returns it.

- **`level_up(self)`**:
  - **What it does**: An abstract method that does nothing in the parent class.
  - **Why?**: It forces every subclass (like `Pawn`) to define its own unique way of leveling up.

### 2. `Pawn` (Concrete Class)
The `Pawn` class inherits from `Player` and represents a specific type of character.

- **`__init__(self)`**:
  - **What it does**: Configures the Pawn.
  - **How?**: Calls `super().__init__()` to setup the path and position, then defines `self.moves` with standard orthogonal directions: Up, Down, Left, Right.

- **`level_up(self)`**:
  - **What it does**: Upgrades the Pawn's abilities.
  - **How?**: Extends the `self.moves` list to include diagonal movements (e.g., `(1, 1)`), allowing the Pawn to move in 8 directions instead of 4.

## Usage Example

```python
pawn = Pawn()           # Create a pawn at (0,0)
pawn.make_move()        # Moves 1 step (Up, Down, Left, or Right)
print(pawn.position)    # Prints new location

pawn.level_up()         # Unlocks diagonal movement
pawn.make_move()        # Can now move diagonally
print(pawn.path)        # Shows the full history of moves
```
