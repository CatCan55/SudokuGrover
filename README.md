# SudokuGrover solves a 4 by 4 Sudoku.

The input is an unsolved Sudoku puzzle. The program reads each entry to determine which boxes are empty. If there are N empty boxes then we need 2N qubits, since each box will be a linear combination of |0> and |1>.

Enumerate going across each row, left to right. 

We need to check when two cells are equal. given a block, check with 3 others in row, 3 others in column, and 1 other in box = 7.
