# Mips-Assembler
this is the assembler for the mips cpu in python

in this project 25 commands have been covered:
add sub addi lw sw lh lhu sh lb lbu sb and or nor andi ori sll srl beq 
bne slt sltu slti j jr jal 

this is the example how to get input :         regisers,numbers(imm in 10 base)
add t1,t2,t3
sub k0,sp,v1
addi v0,t7,55
lw a1,16,a2
sw t0,23,s7
lh t4,102,v0
lhu v1,191,k1
sh t3,3,t9
lb k1,77,s5
lbu t8,2,s6
sb v0,17,v1
and t8,a2,t7
or a0,a1,a2
nor s5,k1,t3
andi t2,s3,5
ori v0,t6,123
sll a1,a2,29
srl a2,a3,12
beq a1,a2,35
bne v1,k1,80
slt a2,t2,s2
sltu s1,a1,t1
slti v0,a2,15
j 9151,0,0
jr a0,0,0
jal 66,0,0

