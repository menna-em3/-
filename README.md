# -
VIRTUAL ROBOT PROGRAMMING
1. Project Overview

This project simulates a virtual autonomous robot navigating in a 2D grid environment using Python.
The robot moves through the environment, avoids obstacles, and attempts to reach a goal. The simulation focuses on algorithmic decision-making, using a Finite State Machine (FSM) for robot behavior.

Key Features:

Grid-based environment with empty cells, obstacles, and a goal.

Robot with position, orientation, and movement states.

Virtual sensors to detect walls, obstacles, and the goal.

Decision-making logic to move toward the goal while avoiding obstacles.

Step-by-step simulation loop with visual display in the console.

2. Environment Setup

The environment is represented by a 2D grid:

Cell Types:

EMPTY – Free space the robot can move.

OBSTACLE – Blocks the robot’s movement.

GOAL – Target location for the robot.

Grid Example:

. . . . . . . . . .
. . . . . . . . . .
. . . # . . . . . .
. . . # . . . . . .
. . . . . . . . G .

. = Empty

# = Obstacle

G = Goal

R = Robot

The robot's initial position is defined when creating the robot object, e.g., (0, 0).

3. Robot Class

The robot has:

Position (x, y)

Direction (NORTH, EAST, SOUTH, WEST)

State (IDLE, MOVING, AVOIDING, FINISHED)

Methods:

turn_left() – Rotates the robot 90° left.

turn_right() – Rotates the robot 90° right.

next_position() – Calculates the next cell coordinates based on direction.

move_forward() – Moves robot to the next cell if it's within bounds and not an obstacle.

sense() – Returns what is in front of the robot: CLEAR, OBSTACLE, WALL, or GOAL.

decide() – FSM-based decision making:

Moves forward if the path is clear.

Turns left or right when facing obstacles or walls.

Stops and prints a message when the goal is reached.

Movement Behavior:

The robot does not move randomly, except when avoiding obstacles it chooses randomly to turn left or right.

It continues moving until it reaches the goal or the maximum steps are reached.

4. Simulation Class

Handles the simulation loop:

Attributes:

environment – The grid environment.

robot – The robot object.

max_steps – Maximum number of steps for simulation.

Methods:

step() – Reads sensor data, executes robot decision, updates steps.

run(delay=0.3) – Displays the grid and robot movement in the console at each step, with a delay.

Ending Conditions:

Simulation stops when:

Robot reaches the goal (RobotState.FINISHED)

Maximum steps are exceeded.

5. How the Robot Moves

Checks the next cell using sense().

If goal ahead → moves forward and finishes.

If clear → moves forward.

If obstacle or wall → chooses randomly left or right, tries to move forward again.

Updates state: MOVING, AVOIDING, or FINISHED.

Note:

The robot may fail to reach the goal if obstacles create an unreachable path or if max_steps limit is too low.

6. How to Run

Copy the code into a Python environment (Google Colab, Jupyter, or local Python 3.x).

Run the script:

python virtual_robot.py

The grid will print to the console each step:

R – Robot

# – Obstacle

G – Goal

. – Empty space

Wait for the simulation to finish. The console will print:

Goal reached!
Simulation finished.
7. Customization

Change grid size: Modify Environment(width, height) in main().

Add/remove obstacles: Change env.grid[y][x] = CellType.OBSTACLE.

Move goal: Change env.grid[y][x] = CellType.GOAL.

Change robot starting position: Modify robot = Robot(x, y).

8. Important Notes

The robot uses FSM-based logic to navigate.

Avoid setting the goal completely blocked by obstacles, or the robot may not reach it.

Delay between steps can be adjusted in sim.run(delay=0.3) for faster/slower visualization.
