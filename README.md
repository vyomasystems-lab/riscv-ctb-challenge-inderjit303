# riscv_ctb_challenges

# Challenge_level1_loop details: 

## Bug explanation with screenshot
The issue lies in the beq instruction used to check if the sum is correct. The beq instruction compares t3 and t4, and if they are equal, it continues with the loop label, which increments t0 and processes the next set of test cases. But, when the sum is correct, the code should jump to the test_end label and pass the test, instead of continuing with the next loop iteration. 

<img width="955" alt="image" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-inderjit303/assets/99788755/f5fed9f7-550a-4aaa-9655-aa13e3d00d6a">


## Screenshot of the fix 

<img width="960" alt="image1" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-inderjit303/assets/99788755/b3741486-d8d3-45b8-8472-aff120edf049">

## Explanation of the fix
To fix the bug, the beq instruction is replaced with a conditional branch to the test_end label when the sum is correct. We can use the bne (branch if not equal) instruction to achieve this. With this change, the code will properly jump to test_end when the sum is correct, and the test will pass as intended.
