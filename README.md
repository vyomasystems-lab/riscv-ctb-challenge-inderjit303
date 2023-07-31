# riscv_ctb_challenges

# Challenge_level2_loop details: 

## Bug explanation with screenshot
The issue lies in the beq instruction used to check if the sum is correct. The beq instruction compares t3 and t4, and if they are equal, it continues with the loop label, which increments t0 and processes the next set of test cases. But, when the sum is correct, the code should jump to the test_end label and pass the test, instead of continuing with the next loop iteration. 

<img width="955" alt="image" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-inderjit303/assets/99788755/f5fed9f7-550a-4aaa-9655-aa13e3d00d6a">


## Screenshot of the fix 
<img width="960" alt="image1" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-inderjit303/assets/99788755/b3741486-d8d3-45b8-8472-aff120edf049">

## Explanation of the fix
To fix the bug, the beq instruction is replaced with a conditional branch to the test_end label when the sum is correct. We can use the bne (branch if not equal) instruction to achieve this. With this change, the code will properly jump to test_end when the sum is correct, and the test will pass as seen in the spike log. 

# Challenge_level3_illegal details: 

## Bug explanation with screenshot
The bug is lies in the order of the instructions. The problem is that the TEST_PASSFAIL directive is placed after the j fail instruction, so the test will always jump to the fail label and not execute the TEST_PASSFAIL directive. 

<img width="930" alt="image2" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-inderjit303/assets/99788755/9d7bf83a-9e94-49c1-8082-0c9c89b546f7">


## Screenshot of the fix 
<img width="930" alt="image3" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-inderjit303/assets/99788755/df29c885-ac23-48ef-884b-173d1e172f55">

## Explanation of the fix
To fix the issue, move the TEST_PASSFAIL directive above the jump instruction. With this change, the program will first set the TESTNUM register to 2, then execute the TEST_PASSFAIL directive, and finally jump to the fail label if an illegal instruction is encountered