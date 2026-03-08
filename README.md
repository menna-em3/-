منة الله عماد الغرة / 120220620
# Virtual Robot Simulation (Python)
Menna Emad ALghorra / 120220620
## 1. Project Overview
This project simulates a **virtual autonomous robot** navigating in a 2D grid environment using Python.  
The robot moves through the environment, avoids obstacles, and attempts to reach a goal. The simulation focuses on algorithmic decision-making, using a **Finite State Machine (FSM)** for robot behavior.

**Key Features:**
- Grid-based environment with empty cells, obstacles, and a goal.
- Robot with position, orientation, and movement states.
- Virtual sensors to detect walls, obstacles, and the goal.
- Decision-making logic to move toward the goal while avoiding obstacles.
- Step-by-step simulation loop with visual display in the console.

---

## 2. Environment Setup
The environment is represented by a 2D grid:

- **Cell Types:**
  - `EMPTY` – Free space the robot can move.
  - `OBSTACLE` – Blocks the robot’s movement.
  - `GOAL` – Target location for the robot.

**Grid Example:**
- `.` = Empty  
- `#` = Obstacle  
- `G` = Goal  
- `R` = Robot

The robot's initial position is defined when creating the robot object, e.g., `(0, 0)`.

---

## 3. Robot Class
The robot has:
- **Position (`x`, `y`)**
- **Direction (`NORTH`, `EAST`, `SOUTH`, `WEST`)**
- **State (`IDLE`, `MOVING`, `AVOIDING`, `FINISHED`)**

**Methods:**
1. `turn_left()` – Rotates the robot 90° left.
2. `turn_right()` – Rotates the robot 90° right.
3. `next_position()` – Calculates the next cell coordinates based on direction.
4. `move_forward()` – Moves robot to the next cell if it's within bounds and not an obstacle.
5. `sense()` – Returns what is in front of the robot: `CLEAR`, `OBSTACLE`, `WALL`, or `GOAL`.
6. `decide()` – FSM-based decision making:
   - Moves forward if the path is clear.
   - Turns left or right when facing obstacles or walls.
   - Stops and prints a message when the goal is reached.

**Movement Behavior:**
- The robot **does not move randomly**, except when avoiding obstacles it chooses randomly to turn left or right.  
- It continues moving until it reaches the goal or the maximum steps are reached.

---

## 4. Simulation Class
Handles the simulation loop:

- **Attributes:**
  - `environment` – The grid environment.
  - `robot` – The robot object.
  - `max_steps` – Maximum number of steps for simulation.

- **Methods:**
  1. `step()` – Reads sensor data, executes robot decision, updates steps.
  2. `run(delay=0.3)` – Displays the grid and robot movement in the console at each step, with a delay.

**Ending Conditions:**
- Simulation stops when:
  1. Robot reaches the goal (`RobotState.FINISHED`)
  2. Maximum steps are exceeded.

---

## 5. How the Robot Moves
1. Checks the next cell using `sense()`.
2. If goal ahead → moves forward and finishes.
3. If clear → moves forward.
4. If obstacle or wall → chooses randomly left or right, tries to move forward again.
5. Updates state: `MOVING`, `AVOIDING`, or `FINISHED`.

**Note:**  
- The robot may fail to reach the goal if obstacles create an unreachable path or if `max_steps` limit is too low.

---

## 6. How to Run
1. Copy the code into a Python environment (Google Colab, Jupyter, or local Python 3.x).  
2. Run the script:
```bash
python virtual_robot.pyGoal reached!
Simulation finished.
