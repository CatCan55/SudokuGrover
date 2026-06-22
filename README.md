# SudokuGrover solves a 4 by 4 Sudoku.

The input is an unsolved Sudoku puzzle at the start of the code called "puzzle". The program reads each entry to determine which boxes are empty. If there are N empty boxes then we need 2N qubits, since each box will be a linear combination of |0> and |1>.

Enumerate going across each row, left to right. Then each column, then each block. Of these 12 constraints, remove the ones that have no empty slot, as these don't need to be checked. In each remaining constraint, check the possible permutations of 1,2,3,4 allowed, and possible solutions in the empty slots, encoded as qubits.

Each time a permutation agrees with the non-empty slots in the given constraint, add that to the list of possible configurations for the constraint. Then check for the qubit slots that are 0 in the possible configuration, and apply the NOT gate. Then apply the multi-controlled NOT gate to switch the ancilla corresponding to that constraint precisely when all controls corresponding to the empty qubits in the given constraint, are 1.

The marker will mark the possible solutions with a phase change of -1.

The diffuser will amplify the probability of solutions that are possible.

The outcome will be the solution in binary for the empty qubits, read right to left.

For emp number of empty slots, it will take about ~pi/4 * 2^{2*emp/2} iterations. For example if emp=3, this is about 6.
