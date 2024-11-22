# README: Virtual/Universal Machine Emulator (with Dynamic Memory Segmentation)

Date: 10/24/23

## PROGRAMMERS: 
Ayah Harper and Nana Adjekum

## PROGRAM PURPOSE:
This program is a Universal Machine (UM) emulator that executes UM instructions. It takes a UM binary file as input, processes the instructions, and executes them in a virtual environment. The emulator supports various operations including arithmetic, logic, memory management, and I/O. It aims to accurately emulate the behavior of a Universal Machine, executing instructions until a halt command is encountered or the program naturally terminates.

## ARCHITECTURE:
- **mainum.c**: Main program entry point. Creates the FILE pointer to read the instruction file.

- **processfile.c** (header: processfile.h): 
  - Processes the input file and loads instructions into memory segments.
  - Uses bitpacking to create work instructions and store them in a sequence.
  - Returns a sequence of segment IDs, including the zero segment and other created segments.

- **execute.c** (header: execute.h):
  - Takes the sequence of segment IDs and executes instructions from the zero segment.
  - Uses bitpacking to extract each instruction and call appropriate functions based on the opcode.

- **instructions.c** (header: instructions.h):
  - Implements individual instruction functions.
  - Takes a struct of memory segments and a bitpacked word containing the opcode and other data.
  - Extracts opcode and other information using bitpacking.

## PERFORMANCE:
The emulator can process approximately 50 million instructions in about 4.7 seconds, based on benchmarks using the midmark.um program.

## UM UNIT TESTS:
The repository includes several unit tests to verify different aspects of the UM emulator:

1. **Basic Operations**: add.um, print-digit.um
2. **Control Flow**: halt.um, halt-verbose.um
3. **Arithmetic**: div-char.um, mult-char.um, mult-OOB.um
4. **Logical Operations**: NAND-nonzero.um, NAND-zero.um
5. **Memory Management**: map-SL.um, map-unmap.um, map-simple.um
6. **Program Loading**: load-prog.um, load-multiple.um, load-PS.um
7. **Input/Output**: input.um
8. **Edge Cases**: div-OOB.um, cmov.um

Each test file focuses on specific instructions or combinations of instructions to ensure correct implementation of the UM specification.

## USAGE:
[Include information on how to compile and run the emulator, along with any command-line arguments or input file formats required.]

## NOTES:
- The emulator uses bitpacking for efficient instruction encoding and decoding.
- Proper error handling is implemented for out-of-bounds operations and invalid instructions.
- The architecture allows for modular development and testing of individual UM components.
