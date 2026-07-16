# SudokuGrover solves a 4 by 4 Sudoku.

The input is an unsolved Sudoku puzzle at the start of the code called "puzzle". Format the sudoku like this

puzzle = [
        [0, 2, 3, 4],
        [3, 4, 0, 2],
        [2, 0, 4, 1],
        [4, 1, 2, 3],
    ]

where numbers 1, 2, 3, 4 are the given entries of the Sudoku and 0 denotes an empty cell. The subsequent part of the program will then be a function of that definition of puzzle.

The program reads each entry to determine which boxes are empty. If there are N empty boxes then we need 2N qubits, since each box will be a linear combination of |0> and |1>.

Enumerate going across each row, left to right. Then each column, then each block. Of these 12 constraints, remove the ones that have no empty slot, as these don't need to be checked. In each remaining constraint, check the possible permutations of 1,2,3,4 allowed, and possible solutions in the empty slots, encoded as qubits.

Each time a permutation agrees with the non-empty slots in the given constraint, add that to the list of possible configurations for the constraint. Then check for the qubit slots that are 0 in the possible configuration, and apply the NOT gate. Then apply the multi-controlled NOT gate to switch the ancilla corresponding to that constraint precisely when all controls corresponding to the empty qubits in the given constraint, are 1.

The marker will mark the possible solutions by flipping the ancillas accordingly. The diffuser will amplify the probability of solutions that are possible with a phase change of -1.

The outcome will be the solution in binary for the empty qubits, read right to left.

For emp number of empty slots, it will take about ~pi/4 * 2^{2*emp/2} iterations. For example if emp=3, this is about 6.

## Acknowledgements

I thank the Erdős Institute's Quantum Computing Bootcamp, under which this program was created.  
