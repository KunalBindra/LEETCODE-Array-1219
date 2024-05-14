# LEETCODE-Array-1219
This code looks like it's solving a problem related to finding the maximum amount of gold that can be collected in a 2D grid, where each cell may contain some amount of gold, and you can move only up, down, left, or right. 

Here's a dry run of how this code works:

1. **getMaximumGold() Method**:
   - Initializes a variable `ans` to store the maximum gold.
   - Loops through each cell in the grid.
   - Calls the `dfs()` method to explore all possible paths starting from each cell and updates `ans` if a higher value is found.
   - Returns the maximum gold amount found.

2. **dfs() Method**:
   - Takes current position `(i, j)` and explores all possible paths from that position.
   - Base cases:
     - If the position is out of bounds or if the cell is empty (contains 0 gold), returns 0.
   - Marks the current cell as visited by setting its value to 0.
   - Recursively explores four directions: up, down, left, and right.
   - Restores the original value of the current cell after backtracking.
   - Returns the maximum amount of gold that can be collected from the current position.

Let's dry run the `dfs()` method on a small grid to see how it works:

```plaintext
Grid:
[[0, 6, 0],
 [5, 8, 7],
 [0, 9, 0]]

Start from position (0, 0)
  - Take 6 gold, mark as visited
  - Move to (1, 0)
    - Take 5 gold, mark as visited
    - Move to (0, 0) -> Already visited, returns 0
    - Move to (2, 0)
      - Take 9 gold, mark as visited
      - Move to (1, 0) -> Already visited, returns 0
      - Move to (2, 1)
        - Take 7 gold, mark as visited
        - Move to (2, 0) -> Already visited, returns 0
        - Move to (2, 2) -> Out of bounds, returns 0
        - Move to (1, 1) -> Out of bounds, returns 0
        - Move to (3, 1) -> Out of bounds, returns 0
        - Move to (2, 3) -> Out of bounds, returns 0
        - Returns 7
      - Move to (1, 1)
        - Already visited, returns 0
      - Move to (2, 2) -> Out of bounds, returns 0
      - Move to (2, 3) -> Out of bounds, returns 0
      - Move to (1, 0) -> Already visited, returns 0
      - Move to (3, 0) -> Out of bounds, returns 0
      - Returns 9
  - Move to (0, 1)
    - Already visited, returns 0
  - Move to (0, -1) -> Out of bounds, returns 0
  - Move to (-1, 0) -> Out of bounds, returns 0
  - Move to (0, 2) -> Out of bounds, returns 0
  - Returns 6

Start from position (0, 1)
  - Already visited, returns 0
```

So, the maximum amount of gold that can be collected from this grid is 9.

The code is working correctly and efficiently explores all possible paths to find the maximum gold amount.
