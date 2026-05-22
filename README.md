# Maze Generator & Solver

A browser-based maze generator and solver built with HTML Canvas and JavaScript.

## How to run
1. Download `maze.html`
2. Open it in Chrome or Firefox
3. Press **Generate Maze** to build a maze
4. Press **Solve Maze** to watch it be solved
5. Tick **Bonus mode** before generating to create loops

## How the generator works
The maze starts as a plain grid where every room has all 4 walls
intact. An invisible mouse is dropped into a random room and uses
a stack-based Depth First Search algorithm to build the maze:

1. Look at all 4 neighbouring rooms
2. If any neighbour is unvisited pick one randomly, knock down
   the wall between them and move there
3. If all neighbours are already visited pop the stack and
   backtrack to the previous room
4. Repeat until every room has been visited

This guarantees a proper maze where every room connects to every
other room by exactly one unique path.

## Data structure
The maze is stored in two 2D arrays:
- `northWall[r][c]` — true if the top wall of room (r,c) is intact
- `eastWall[r][c]`  — true if the right wall of room (r,c) is intact

## How the solver works
The solver uses the same backtracking approach:
- A red dot marks rooms on the current active path
- A blue dot marks rooms that were tried but led to dead ends
- The solver backtracks whenever it hits a dead end and keeps
  going until it reaches the exit

## Bonus mode
When bonus mode is enabled the mouse has a 1 in 20 chance of
eating an extra random wall during generation. This creates loops
in the maze which breaks the classic shoulder to the wall rule.


