# MIPS Assembler

A small Python-based assembler for a subset of MIPS instructions. The script reads assembly instructions from `input.txt`, converts each instruction into a 32-bit binary machine-code string, and prints the result to the terminal.

This is a course-style assembler project focused on instruction encoding logic. It does not parse full MIPS source files with labels, sections, comments, or directives.

## Features

- Converts supported MIPS instructions to binary machine code
- Reads multiple instructions from `input.txt`
- Prints each converted instruction as `[instruction, machine_code]`
- Supports R-type, I-type, and J-type instruction formats
- Includes an example input file
- Uses only the Python standard library

## Supported Instructions

The assembler currently supports 26 MIPS instructions:

```text
add  sub  addi
lw   sw   lh   lhu   sh   lb   lbu   sb
and  or   nor  andi  ori
sll  srl
beq  bne
slt  sltu slti
j    jr   jal
```

## Project Structure

```text
.
+-- Assembler.py          # Main assembler script
+-- input.txt             # Sample input instructions
+-- howToGetInputs.txt    # Input-format examples
+-- README.md
```

## Input Format

Each line in `input.txt` should contain one instruction.

Registers are written without `$`, operands are comma-separated, and immediates are decimal numbers.

Examples:

```text
add t1,t2,t3
addi v0,t7,55
lw a1,16,a2
beq a1,a2,35
j 9151,0,0
jr a0,0,0
jal 66,0,0
```

For load/store instructions, the project uses this simplified operand order:

```text
instruction target_register,offset,base_register
```

For jump instructions, the script still expects three comma-separated operands after the command, so unused operands are written as `0`.

## How to Run

Install Python 3, edit `input.txt`, then run:

```bash
python3 Assembler.py
```

Example output:

```text
['add', '00000001010010110100100000100000']
['addi', '00100001111000100000000000110111']
['j', '00001000000000000010001110111111']
```

## How It Works

`Assembler.py` contains:

- `commandsOpCodes`: opcode mapping for supported instructions
- `registersValue`: register-name to binary-number mapping
- `assembler(command, operator1, operator2, operator3)`: instruction encoder
- file-reading logic that loads `input.txt`, parses each line, encodes it, and prints the result

The script manually builds binary strings by concatenating opcode, register fields, shift amount, function code, and immediate/address bits depending on the instruction.

## Notes

- Input parsing is intentionally simple and expects the exact format shown above.
- Labels, `.data`, `.text`, comments, pseudo-instructions, and symbolic branch targets are not supported.
- Immediate and address values are expected to be decimal numbers.
- Negative immediates are not handled as two's-complement values.
- Output is printed to the terminal and is not written to a file.
- The assembler uses register names such as `t0`, `s1`, `a0`, `sp`, and `ra` without the `$` prefix.

## Possible Improvements

- Add support for labels and branch/jump label resolution
- Add comment and blank-line handling
- Add two's-complement encoding for negative immediates
- Write output to a file
- Add validation and clearer error messages
- Add automated tests for each instruction format
- Support standard MIPS memory syntax such as `lw t0, 4(sp)`
