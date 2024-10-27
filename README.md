# LEETCODE-TREES-1277
Let's walk through a dry run of the `countSquares` method step by step with an example matrix to understand its logic. The method counts the number of square submatrices filled with `1`s in a given binary matrix.

### Dry Run Example

Consider this input matrix:

\[
\begin{bmatrix}
1 & 0 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1 \\
\end{bmatrix}
\]

### Code Explanation
- The code uses a dynamic programming (DP) approach, modifying the matrix in place.
- The DP rule applied is:
  - If a cell `(i, j)` has a `1` and is not on the first row or first column, its value becomes the size of the largest square submatrix ending at that cell.
  - The value at `(i, j)` will be `1 + min(matrix[i-1][j-1], matrix[i-1][j], matrix[i][j-1])`, which represents the largest possible square that can end there.
- Finally, we sum up all values in the matrix. Each entry represents the count of squares ending at that position.

### Step-by-Step Execution
Starting with the input matrix:

\[
\begin{bmatrix}
1 & 0 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1 \\
\end{bmatrix}
\]

Let's go through each cell that might be updated:

1. **Cell (0,0)**: 
   - It's on the first row, so we leave it as `1`.

2. **Cell (0,1)**:
   - Value is `0`, so we skip it.

3. **Cell (0,2)**:
   - It's on the first row, so it stays as `1`.

4. **Cell (1,0)**:
   - It's on the first column, so it remains `1`.

5. **Cell (1,1)**:
   - It has `1`, and `i > 0`, `j > 0`.
   - Update it to `1 + min(matrix[0][0], matrix[0][1], matrix[1][0])` = `1 + min(1, 0, 1)` = `1`.

6. **Cell (1,2)**:
   - It has `1`, and `i > 0`, `j > 0`.
   - Update it to `1 + min(matrix[0][1], matrix[0][2], matrix[1][1])` = `1 + min(0, 1, 1)` = `1`.

7. **Cell (2,0)**:
   - It's on the first column, so it remains `1`.

8. **Cell (2,1)**:
   - It has `1`, and `i > 0`, `j > 0`.
   - Update it to `1 + min(matrix[1][0], matrix[1][1], matrix[2][0])` = `1 + min(1, 1, 1)` = `2`.

9. **Cell (2,2)**:
   - It has `1`, and `i > 0`, `j > 0`.
   - Update it to `1 + min(matrix[1][1], matrix[1][2], matrix[2][1])` = `1 + min(1, 1, 2)` = `2`.

The updated matrix becomes:

\[
\begin{bmatrix}
1 & 0 & 1 \\
1 & 1 & 1 \\
1 & 2 & 2 \\
\end{bmatrix}
\]

### Sum Calculation

Now, summing up all the elements gives:

\[
1 + 0 + 1 + 1 + 1 + 1 + 1 + 2 + 2 = 10
\]

### Final Result

The function will return `10`, which is the total count of square submatrices filled with `1`s.
