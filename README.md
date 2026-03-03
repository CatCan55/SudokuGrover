# SudokuGrover solves a 4 by 4 Sudoku.

# Board has 16 boxes. each box is a number from 1 to 4. 
# A 2-qubit has a basis of 4 elements. So need 32 qubits since each box needs
# 2 qubits. enumerate going across each row, left to right. 

# Put four numbers on the board - do 1 (00), 2 (01), 3 (10), 4 (11) across top row

# We need to check when two cells are equal
# given a block, check with 3 others in row, 3 others in column, and 1 other in box = 7
# have 16*7 = 112 boxes, and each pair then counted twice so just need 56

### I'm not sure how to check pairs. 
# for each cell I need to check if it equals any of the others in the box, 
# across the row, and down the column. so for [0] and [1] I set it to 00 state 
# which is 1. then I need to check if [2-3], [4-5], [6-7] are in 00, then 
 # [8-9], [16-17], and [24-25], and then the one diagonal down which is [10-11]. 
 # how to automate that?
