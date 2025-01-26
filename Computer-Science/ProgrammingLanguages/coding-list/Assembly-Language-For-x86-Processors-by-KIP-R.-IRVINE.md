# Assembly Language for x86-64 Processors

## ASCII Control Characters
- ASCII Codes generated when a control key combination is pressed. 
| ASCII Code* | Ctrl-    | Mnemonic | Description            |
| ----------- | -----    | -------- | -----------            |
| 00          |          | NULL     | Null Character         |
| 01          | Ctrl-A   | SOH      | Start of Header        |
| 02          | Ctrl-B   | STX      | Start of Text          |
| 03          | Ctrl-C   | ETX      | End of Text            |
| 04          | Ctrl-D   | EOT      | End of Transmission    |
| 05          | Ctrl-E   | ENQ      | Enquiry                |
| 06          | Ctrl-F   | ACK      | Acknowledge            |
| 07          | Ctrl-G   | BEL      | Bell                   |
| 08          | Ctrl-H   | BS       | Backspace              |
| 09          | Ctrl-I   | HT       | Horizontal Tab         |
| 0A          | Ctrl-J   | LF       | Line Feed              |
| 0B          | Ctrl-K   | VT       | Vertical Tab           |
| 0C          | Ctrl-L   | FF       | Form Feed              |
| 0D          | Ctrl-M   | CR       | Carriage Return        |
| 0E          | Ctrl-N   | SO       | Shift Out              |
| 0F          | Ctrl-O   | SI       | Shift In               |
| 10          | Ctrl-P   | DLE      | Data Link Escape       |
| 11          | Ctrl-Q   | DC1      | Device Control 1       |
| 12          | Ctrl-R   | DC2      | Device Control 2       |
| 13          | Ctrl-S   | DC3      | Device Control 3       |
| 14          | Ctrl-T   | DC4      | Device Control 4       |
| 15          | Ctrl-u   | NAK      | Negative Acknowledge   |
| 16          | Ctrl-V   | SYN      | Synchronous Idle       |
| 17          | Ctrl-W   | ETB      | End transmission block |
| 18          | Ctrl-X   | CAN      | Cancel                 |
| 19          | Ctrl-Y   | EM       | End of Medium          |
| 1A          | Ctrl-Z   | SUB      | substitute             |
| 1B          | Ctrl-I   | ESC      | Escape                 |
| 1C          | Ctrl-\   | FS       | File Seperator         |
| 1D          | Ctrl-]   | GS       | Group Seperator        |
| 1E          | Ctrl-^   | RS       | Record Seperator       |
| 1F          | Ctrl-(-) | US       | Unit Seperator         |
| ----------- | -------- | -------- | ---------------------- |
* ASCII Codes are in hexadecimal
## Alterative Key Combinations
- Following are hexadecimal scan codes produced by holding down the ALT key and pressing each character:
| Key | Scan Code |
| --- | --------- |
| 1   | 78        |
| 2   | 79        |
| 3   | 7A        |
| 4   | 7B        |
| 5   | 7C        |
| 6   | 7D        |
| 7   | 7E        |
| 8   | 7F        |
| 9   | 80        |
| 0   | 81        |
| -   | 82        |
| =   | 83        |
| A   | 1E        |
| B   | 30        |
| C   | 2E        |
| D   | 20        |
| E   | 12        |
| F   | 21        |
| G   | 22        |
| H   | 23        |
| I   | 17        |
| J   | 24        |
| K   | 25        |
| L   | 26        |
| M   | 32        |
| N   | 31        |
| O   | 18        |
| P   | 19        |
| Q   | 10        |
| R   | 13        |
| S   | 1F        |
| T   | 14        |
| U   | 16        |
| V   | 2F        |
| W   | 11        |
| X   | 2D        |
| Y   | 15        |
| Z   | 2C        |
| --- | --------- |

## Keyboard Scan Codes: 
The following keyboard scan codes may be trieved either by invoking INT 16h or by callng INT 21h for keyboard input a second time (first keyvoard read returns 0). All codes are in hexadecimal: 
### Function Keys
| Key | Normal | With Shift | With Ctrl | With Alt |
| --- | ------ | ---------- | --------- | -------- |
| F1  | 3B     | 54         | 5E        | 68       |
| F2  | 3C     | 55         | 5F        | 69       |
| F3  | 3D     | 56         | 60        | 6A       |
| F4  | 3E     | 57         | 61        | 6B       |
| F5  | 3F     | 58         | 62        | 6C       |
| F6  | 40     | 59         | 63        | 6D       |
| F7  | 41     | 5A         | 64        | 6E       |
| F8  | 42     | 5B         | 65        | 6F       |
| F9  | 43     | 5C         | 66        | 70       |
| F10 | 44     | 5D         | 67        | 71       |
| F11 | 85     | 87         | 89        | 8B       |
| F12 | 86     | 88         | 8A        | 8C       |
| --- | ------ | ---------- | --------- | -------- |

| Key      | Alone | With Ctrl Key |
| -------- | ----- | ------------- |
| Home     | 47    | 77            |
| End      | 4F    | 75            |
| PgUp     | 49    | 84            |
| PgDn     | 51    | 76            |
| PrtSc    | 37    | 72            |
| Lt Arrow | 4B    | 73            |
| Rt Arrow | 4D    | 74            |
| Up Arrow | 48    | 8D            |
| Dn Arrow | 50    | 91            |
| Ins      | 52    | 92            |
| Del      | 53    | 93            |
| Back Tab | 0F    | 94            |
| Gray +   | 4E    | 90            |
| Grey -   | 4A    | 8E            |
| -------- | ----- | ------------- |

# Content For x86_64 Assembly 

## Contents 
1. Basic Concepts 
   

## Preface 
### Chapter Descriptions and Layout
Chapters 1-8 contain core concepts for assembly, and should be covered in a sequence. After those chapters you have a fair amount of freedom. The following chapter dependency graph shows how later chapters depend on knowledge gained from other chapters. 
- Chapter Dependency Graph: 
  * Chapter's 1-9
    * Chapter 10 
        * Chapter 11-14 
    * Chapter 15
        * Chapter 16-17
- Chapter Descriptions: 
    1. Basic Concepts: Applications of assembly language, basic concepts, machine language, and data representation. 
    2. x86 Processor Architecutre: Basic Microcomputer design, instrution execution cycle, x86 processor architecture, Intel64 Architecute, x86 memory management, components of a microcomputer, and the input-output system. 
    3. Assembly Language Fundamentals: Introducton to assembly language, linking, and debugging, and defining constants and variables.
    4. Data Transfers, Addressing, and Arithmetic: Simple data transfer and arithmetic instructions, assemble-link-execute cycle, operators, diectives, expressions, JMP and LOOP instructions, and indirect addressing.
    5. Procedures: Linking to an external library, description of the book/s link library, stack operations, defining and using procedures, flowcharts, and top-down structured design.
    6. Conditional Processing: Boolean and Comparison instructions, conditional jumps, and loops, high-level logic structures, and finite-state machines.
    7. Integer Arithmetic: Shift and Rotate instructions with useful applications, multiplcations, and divisions, extended addition and subtraction, and ASCII, and packed decimal arithmetic.
    8. Advanced Procedures: Stack parameters, local variables, advanced PROC and INVOKE directives, and recursion.
    9. Strings and Arrays: String primitives, manipulating arrays of characters and integers, two-dimensional arrays, sorting and searching.
    10. Structures and Macros: Structures, macros, conditional assembly directives, and defining repeat blocks. 
    11. MS-Windows Programming: Protected mode memory management copcepts, using the microsoft-Windows API to display text and colors, and dynamic memory allocations (I will try to integrate Fb here for linux systems).
    12. Floating-Point Processing and Instruction Encoding: Floating-point binary representation and floating-point arithmetic. Learning to program the IA-32 floating-point unit. Under standning the encoding of IA-32 machie instructions.
    13. High-Level Language Interface: Parameter passing conventions, inline assembly code, and linking assembly language modules to C and C++ programs. 
    14. 16-bit MS-DOS programming: Memory organization, interuppts, function calls, and standard MS-DOS file I/O services.
    15. Disk Fundamentals: Disk storage systems, sectors, clusters, directories, file allocation tables, handling MS-DOS error codes, and drive directory manipulation. 
    16. BIOS-Level Programming: Keyboard inpu, videotext, graphics, and mouse programming. 
    17. Exper MS-Ds Programming: Custom-designed segments, runtime program structure, and interrupt handling. 
       
# Chapter 1 - Basic Concepts 
## 1.1 Welcome to Assembly Language
- The book recommends MASM or the Microsoft Macro ASsembler. However, I don't use windows because windows is gay, so I will be using NASM. 
- Assembly language is the oldest programming language, and of all the languages, bears the closest resemblance to native machine language. It provides direct access to computer hardware, thus requiring an understanding of your computer's architecture, and operating system. 
- Ontop of being the oldest language, Assembly is not a uniform, concrete language. There are different Instruction Set Architectures or ISA's to dictate the syntax and language of the machine. x86 is one of these architectures, the 64 refers to the register bit capacity. This makes assembly a not-portable language. A language who's source code can be compiled and run on a variety of different machines is said to be portable. Assembly by definition is specific for a processor family. The instructions in assembly may directly match the computer's architecture or they may be translated during execution by a program inside the processor known as a microcode interpreter.
- Relation of Assembly to higher level programming languages and machine language: 
  * Machine language is a numeric language specifically understood by the computer's CPU / processor. All x86 processors understand a common machine language. Assembly language consists of statements written with short mnemonics such as ADD, MOV, SUB, and CALL. Assembly has a 1:1 relationship to machine language. 
  * High-level languages such as Python, Clangs, Java, etc, have a 1:many relationship with assembly and machine language. A single statement in C++ for example, expands into multiple assembly language or machine instructons. Most people cannot read raw machine code, so we examine it's closest relative, Assembly. For example, here is a convertion between C++ and Assembly: 
    * C++
        * int y;  
        * int x = (y + 4) * 3;
    * Asm 
        * mov eax,y     ;move y to the EAX reg 
        * add eax,4     ;Add 4 to the EAX reg  
        * mov ebx,3     ;move 3 to the EBX register  
        * imul ebx      ;Multiply EAX by EBX
        * mov X,eax     ;Move EAX to X
(Registers are named storage locations in the CPU holding intermediate results of operations.)  
   
   
   
   
   
   
   
   





