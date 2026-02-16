# Player Interface Documentation
# ♟️ Random Pawn Movement – Explanation Guide

## 📌 Overview

This project simulates a simple **Pawn** moving randomly on a 2D grid using Object-Oriented Programming concepts like **abstraction**, **inheritance**, and **method overriding**.

Each move:

* Selects a random direction
* Updates the pawn’s position
* Stores the full movement path

The pawn starts at coordinate `(0,0)`.

---

# 🧱 Class Structure

## 1️⃣ `Player` (Abstract Base Class)

The `Player` class acts as a blueprint for all future player types.

### Initialization

```python
self.moves = []
self.position = (0,0)
self.path = [self.position]
```

Explanation:

* **moves** → list of allowed directions.
* **position** → current location of the player.
* **path** → history of all visited positions.

---

### 🎲 `make_move()` Method

```python
move = random.choice(self.moves)
new_position = (
    self.position[0] + move[0],
    self.position[1] + move[1]
)
```

This is the core logic of the program.

#### Step-by-Step Logic

1. Choose a random move from allowed moves.
2. Add the movement values to the current coordinates.
3. Save the new position in the path.
4. Update the player’s current position.
5. Return the updated position.

#### Coordinate Formula

```
new_position = (current_x + move_x,
                current_y + move_y)
```

This is simple **vector addition** on a grid.

---

### 🔒 Abstract Method

```python
@abstractmethod
def level_up(self):
    pass
```

Any subclass must implement its own `level_up()` behavior.

---

## 2️⃣ `Pawn` Class (Child Class)

The `Pawn` inherits all movement logic from `Player`.

### Initial Moves

```python
self.moves = [(0,1),(0,-1),(1,0),(-1,0)]
```

Meaning:

* `(0,1)`  → move up
* `(0,-1)` → move down
* `(1,0)`  → move right
* `(-1,0)` → move left

---

### 🚀 `level_up()` Method

```python
self.moves.extend([(1,1),(1,-1),(-1,1),(-1,-1)])
```

After leveling up, diagonal moves are added:

* `(1,1)`   ↗
* `(1,-1)`  ↘
* `(-1,1)`  ↖
* `(-1,-1)` ↙

---

# ▶️ Program Execution

```python
pawn = Pawn()
for _ in range(5):
    print(pawn.make_move())
```

Process:

1. Pawn starts at `(0,0)`.
2. Loop runs 5 times.
3. Each iteration randomly selects a move.
4. Position updates and prints.

---

# 📊 Example Walkthrough

Example Output:

```
(0, 1)
(1, 1)
(1, 0)
(2, 0)
(2, -1)
```

### Move 1

Current position: `(0,0)`
Random move: `(0,1)`

```
new_x = 0 + 0 = 0
new_y = 0 + 1 = 1
```

Updated position → `(0,1)`

---

### Move 2

Current position: `(0,1)`
Random move: `(1,0)`

```
new_x = 0 + 1 = 1
new_y = 1 + 0 = 1
```

Updated position → `(1,1)`

---

### Move 3

Current position: `(1,1)`
Random move: `(0,-1)`

```
new_x = 1 + 0 = 1
new_y = 1 - 1 = 0
```

Updated position → `(1,0)`

---

### Move 4

Current position: `(1,0)`
Random move: `(1,0)`

```
new_x = 1 + 1 = 2
new_y = 0 + 0 = 0
```

Updated position → `(2,0)`

---

### Move 5

Current position: `(2,0)`
Random move: `(0,-1)`

```
new_x = 2 + 0 = 2
new_y = 0 - 1 = -1
```

Updated position → `(2,-1)`

---

# 🧠 Core Concept Summary

* Movement is just **adding tuples**.
* `(x,y)` represents position.
* `(dx,dy)` represents direction.
* New position = `(x+dx, y+dy)`.

---

# 🧭 Visual Path Example

```
Start -> (0,0)
   ↓
(0,1)
   →
(1,1)
   ↓
(1,0)
   →
(2,0)
   ↓
(2,-1)
```

---

# ✅ Key Learning Points

* Use of Abstract Base Classes (`ABC`)
* Method overriding
* Random movement simulation
* Tuple indexing (`[0]`, `[1]`)
* Position tracking with lists

---

# 🚀 Possible Future Improvements

* Call `level_up()` to unlock diagonal movement.
* Print chosen move each turn for debugging.
* Plot pawn path visually on a grid.
* Add multiple player types.

---

**Author Note:**
This project demonstrates how abstraction and coordinate math combine to create a simple movement engine using Python OOP principles.
