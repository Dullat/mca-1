# Instruction Cycle in Computer Architecture

The instruction cycle, also known as the fetch-decode-execute cycle or fetch-and-execute cycle, is the fundamental operation of a computer’s central processing unit (CPU). It is the sequence of steps the CPU follows to execute each machine language instruction.

The instruction cycle consists of four main phases:

1. **Fetch**: The CPU retrieves an instruction from memory and places it in the instruction register.
2. **Decode**: The CPU analyzes and decodes the instruction to determine what operation needs to be performed, such as a memory reference, register operation, or I/O access.
3. **Operand Fetch**: Depending on the instruction, the CPU may need to fetch operands (data) from memory, registers, or I/O devices.
4. **Execute**: The CPU performs the actual operation specified by the instruction, using the fetched operands.

This cycle is repeated for each instruction in a program, allowing the CPU to execute a series of instructions to perform a specific task. The instruction cycle is the basic building block of computer execution, enabling the CPU to carry out the instructions that make up a program.