This is a processor I created so that I can follow along with some of the concepts in `Computer Architecture: A Quantitative Approach` by John Hennessy and David Patterson. I have also put together a simple ISA (described in `ISA attempt rriscv.xlsx`) and assembler to go along with it. I have also written a stack based virtual machine compiler inspired by the one in the `nand2tetris` series but with a slightly different hardware level implementation/memory layout.

Processor features include:
- 32 bit
- 5 stage pipeline (IF, ID, EX, MEM, WB)
- 32 registers
- 32 implemented opcodes (up to 64)
- Register forwarding/bypassing

VM compiler features include:
- Push/pop operations
- temp, static, result, local, argument, "this", and "that" segments in memory that push/pop can use
- Labels, conditional label jumps
- Functions, calls, returns

Descriptions of op-codes and registers can be found in `ISA attempt rriscv.xlsx`. There are only two types of instrucions, being the one listed in that spreadsheet and one which merges the imm and rd fields into an immRD field which is just a longer immediate (this is subject to change, I will probably add more).

The assembler uses the same format for instruction parameters defined in the spreadsheet. 

__log__

Update #1: Forwarding/bypassing has been added.

Update #2: `rriscvmcompiler.py` contains the start of a compiler for a stack based byte code language. Currently only `push (segment) (index)`, `pop (segment) (index)`, and basic arithmetic operations are implemented. This will be based off of the language used in the `nand2tetris` lecture notes.

Update #3: added `label`, `goto`, `if-goto` (pops top of stack and checks if it should jump) to byte language. At some point, I may restructure the way instructions are defined to allow for bigger fields when the others are not needed (other than just immRD).

Updte #4: added `function`, `call`, and `return` along with logic for the call stack. Memory layout documented in the spreadsheet.
