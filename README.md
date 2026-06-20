# SudokuGrover solves a 4 by 4 Sudoku.

The input is an unsolved Sudoku puzzle. The program reads each entry to determine which boxes are empty. If there are N empty boxes then we need 2N qubits, since each box will be a linear combination of |0> and |1>.

Enumerate going across each row, left to right. Then each column, then each block. In each constraint, check the possible permutations of 1,2,3,4 allowed, and possible solutions in the empty slots, encoded as qubits.
