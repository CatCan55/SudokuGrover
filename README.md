# SudokuGrover solves a 4 by 4 Sudoku.

## Step 1

The input is an unsolved Sudoku puzzle at the start of the code called "puzzle". Format the sudoku like this

puzzle = [
        [0, 2, 3, 4],
        [3, 4, 0, 2],
        [2, 0, 4, 1],
        [4, 1, 2, 3],
    ]

where numbers 1, 2, 3, 4 are the given entries of the Sudoku and 0 denotes an empty cell. The subsequent part of the program will then be a function of that definition of puzzle.

## Step 2

The program reads each entry to determine which boxes are empty. If there are N empty boxes then we need 2N qubits, since each box will be a linear combination of |0> and |1>.

## Step 3 & 4: constraints & ancillas

Enumerate going across each row, left to right. Then each column, then each block. Of these 12 constraints, remove the ones that have no empty slot, as these don't need to be checked. So we have at most 12 ancillas, one per constraint.

In each remaining constraint, check the possible permutations of 1,2,3,4 allowed, and possible solutions in the empty slots, encoded as qubits. Each time a permutation agrees with the non-empty slots in the given constraint, add that to the list of possible configurations for the constraint. Then check for the qubit slots that are 0 in the possible configuration, and apply the NOT gate. Then apply the multi-controlled NOT gate to switch the ancilla corresponding to that constraint precisely when all controls corresponding to the empty qubits in the given constraint, are 1. 

## Step 5

The marker circuit will then mark the possible solutions with a -1. 

## Step 6

The diffuser will amplify the probability of solutions that have been marked.

## Step 7

The outcome of the Grover circuit will be the solution in binary for the empty qubits, read right to left.

For emp number of empty slots, it will take about ~pi/4 * 2^{2*emp/2} iterations. For example if emp=3, this is about 6.

## Step 8

Convert the solution to the solved Sudoku board.

## Acknowledgements

I thank the Erdős Institute's Quantum Computing Bootcamp, under which this program was created.  
