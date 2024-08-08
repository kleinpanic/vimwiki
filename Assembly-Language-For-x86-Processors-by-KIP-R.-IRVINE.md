# Assembly Language for x86 Processors by KIP R. IRVINE
## Table of Contents:

## 1. Basic Concepts:
### 1.1 Welcome to Assembly Language
    Assembly language for x86 Processors focuses on programming microprocessors compatible with Intel and AMD processors running under 32-Bit and 64-bit versions of MS. The latest version of Microsoft Macro Assembler (MASM), is used in reference with the book. MASM is included with MS Version Studio. Some other well known assemblers for x86 systems running under microsoft windows include TASM (Turbo Assembler), NASM (Network ASsembler), and MASM32 (Variant of MASM). 2 popular linux based assemblers are GAS (GNU ASsembler), and NASM, of those NASM's syntax is most similar to that of MASM. 
    Assembly language is the oldest programming language and of all the languages, bears the closest resemblance to native machine language. It provides direct access to computer hardware requiring you to understand much about your computer's architecture and operating system.
#### 1.1.1 Questions you might ask (Summarized)
- What are assemblers and linkers?
    An assembler is a utility program that converts source code programs from assembly language into machine language. A linker is a utility program that combines individual files created by an assembler to a single executable program. A related utility, called a debugger, lets you step through a program while its running and examine registers and memory. 
- Hard and software needed?
    A compiler that runs a 32 or 64 bit version of MS (prefered by book) but we finna use linux 
- Types of programs can be created using MASM / NASM?
    32-bit Protected mode: Run under all 32-bit versions of MS (We use linux i assume its the same)
    64-bit mode: run under all 64-bit 
    16-bit mode: runs under 32 bit versions and on embedded systems. Not on 64. 
- Relation of assembly to machine language?
    Machine language is a numeric language specifically understood by computer's processor (the CPU). All x86 processors understand a common achine language. Assembly language consists of statements written with short mnemonics such as ADD, MOV, SUB, IMUL, and CALL. ASsembly language has a one to one relationship with machine languages. Each assembly instruction corresponds to a singular machine language instruction. 
    High level languages such as Python, C++, C, and Java, have a one to many relationship with assembly language and machine language. A singualr statement expands into multiple assembly language or machine instruction. Most people cannot read raw machine code, so this book examines its closest relative, assembly. Example of C++ code that carries out two arithmetic operations and assigns the results to a variable. Assume X and Y are integrers:
        int Y;
        int X; = (Y + 4) * 3;
    Equivalent translation to assembly. Translation requires multiple statements because each assembly language statement corresponds to a singular machine instruction:
        mov eax,Y               ; move Y to the EAX register
        add eax,4               ; add 4 to the EAX register
        mov ebx,3               ; move 3 to the EBX register
        imul ebx                ; multiply EAX by EBX
        mov X,ebx               ; move EAX to variable X 
(Registers are named storage locations in the CPU that hold intermediate results of operations.) Assembly is not portable, because it is designed for a specific processor family. THere are a number of different assembly languages, each based on a processor family. 

#### 1.1.2 Assembly Language Aplications
    Historically, in the early ages of programming, most applications were written partially, or entirely in assembly language. THey had to fit in a small area of memory and run as efficiently as possible on slow processors. As memory became more plentiful and processors dramatically increased in speed, programs became more complex. Programmers switched to high-level languages such as C, Fortran, and COBOL, that contained a certain amount of structuring capability. More recently, object oriented languages such as Pyhton, C++, C#, and Java, have made it possible to write compelx programs containig millions ofl ines of code. 
    1.1 Comparison of Assembly language to High Level languages
| Type of Application                                                   | High-Level Languages                                                                                                                                        | Assembly Language                                                                                                                                            |
|-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Comm/sci app written for single platform M to L size.                 | Formal structures make it easy to organize and maintain large sections of code.                                                                             | Minimal formal structure, so one must be imposed by programmers who have varying levels of experience. This leads to difficulties maintaining existing code. |
| Hardware device driver                                                | The language may not provide for direct hardware access. Even if it does, awkward coding techniques may be required, resulting in maintenance difficulties. | Hardware access is straightforward and simple. Easy to maintain when programs are short and well documented.                                                 |
| Comm/scien app written for mult. platforms (diff OSs)                 | Usually portable. The source code can be recompiled on each target operating system with minimal changes.                                                   | Must be recoded separately for each platform, using an assembler with a different syntax. Difficult to maintain.                                             |
| Embedded systems and computer games requiring direct hardware access. | May produce large executable files that exceed the memory capacity of the device.                                                                           | Ideal, because the executable code is small and runs quickly.                                                                                                |
### 1.2 Virtual Machine Concepts
    An effective way to explain how a computer's hardware and software are related is called the virtual machine concept. Let us begin with the most basic function of a computer, executing programs. 
        A computer can usually execute programs written in its native machine language. Each instruction in this language is simple enough to be executed using a relatively small numbder of electronic circuits. For simplicity, we will call this language L0. 
        Programmers would have a difficult time writing programs in L- because it is enormously detailed and consists purely of numbers. If a new language, L1, could be constructed that was easier to use, programs could be written in L1. There would be two ways to achieve this:
        1. Interpretion: as the L1 prgram is running, each of its instructions could be decoded and executed by a program written in language L0. The L1 program begins running immediately but each instruction has to be decoded before it can execute. 
        2. Translation: The entire L1 program could be converted into an L0 program by an L0 program specifically designed for this purpose. Then, the resulting L0 program could be executed directly on the computer hardware.
*Virtual Machines*
Rather than using only languages, it is easier to think in terms of a hypotheticaly computer, or virtual machine, at each level. Informally, we can define a virtual machine as a software program that emulates the functions of some other physical or virtual computer. The virtual machine, VM1, as we will refer to it as, can execute commands written in language L1. The virtual machine VM0 can execute commands written in language L0.
Each virtual machine can be constructed for either hardware or software. People can write programs for virtual machine VM1, and if it is practical to implement VM1 as an actual computer, programs can be executed directly on the hardware. Or programs written in VM1 can be intepreted/translted and executed on VM0.
Machine VM1 cannot be radically different from VM0 bc the translation or intepreation would be too time-consuming. What if the language VM1 supports is not programmer-friendly enought to be used for useful applications? Then another virtual machine VM2, can be designed that is more easily understood. This procress can be repeated untila virtual machine VMn can be designed to support a powerful, easy to use language. 
    The Java programming language is based on the virtual machine concept. A program written in the java language is translated by a Java compiler into Java Byte Code.The latter is a low level language quicklyexecuted atruntime by a program known as a Java Virtual Machine (JVM). The JVM has been implemented on many different computer systems making java programs relatively system independent. 
*Specific Machines*
Let use related to to an actual computer and languages, using namessuch as Level 2 for VM2 and Level 1 for VM1. A computer,s digital logic hardware represents machine level 1. Above this is level 2, called the instruction set architecture (ISA). This is the first level at which users can typically write programs,althought the programs consist of binary values called machine language. 
Digital Logical (Level 1):
Instruction Set Architecture (Level 2):
    Computer chip manufacturers design into the processor an instruction set to carry out basic operations, such as move, add, or multiply. This set of instructions is also referred to as machine language. Each machine-language instruction is executed either directed by the computer's hardware or by a program embedded in the microprocessors chip called a microprogram.
Assembly Language (Level 3):
    Above the ISA level, programming language provide translation layers to make large-scale software development practical. ASsembly language, which appears at level 3, uses short mnemonics such as ADD, SUB, and MOV, which are easily translated into the ISA level (1-1 relationship). Assembly language programs are translated (assembled) in their entirety into machine language before they begin to execute. 
High Level language (level 4):
    at level 4 are high level programming languages such as C, C++, and Java. Programs in these languages contain powerful statements that translate into multiple assembly language instructions. You can see such a translation, for example, by examining the listing file output created by a C++ compiler. The assembly language is automatically assembled by the compiler into machine language. 
### 1.3 Data Representation
Assembly language programmers deal with data at the physical level, so they must be adept at examining memory and registers. Often,binary numbers are used to describe the contents of computer memory; at the other time, decimal and hexadecimal numbers are used. You must develop a certain fluency with number formats so you can quickly translate numbers from one format to another. 
    Each numbering format or system, has a base, or maximum numberof symbols that can assigned to a single digit. The possible digits for the numbering systems used most commonly in hardware and software manuals is below, the last row, hexadecimal numbers use digits 0-0 and continue with the letters A through F to represents values 10 through 15. it is quite commmoned to use these numbers when showing the contents of computer memory and machine-level instructions.
    Table 1.2 Binary, Octal, Decimal, and Hexadecimal Digits.
| System      | Base | Possible Digits  |
|-------------|------|------------------|
| Binary      | 2    | 0 1              |
| Octal       | 8    | 0 1 2 3 4 5 6 7  |
| Decimal     | 10   | 0123456789       |
| Hexadecimal | 16   | 0123456789ABCDEF |
|-------------|------|------------------|

#### 1.3.1 Binary integrers
A computer stores instructions and data in memory as collections of electronic charges. Representing these entities with numbes requires a system geared to the concet of on and off, true and false, or binary. Binary numbers are base 2 numbers, in which each binary digit (called a bit) is either 0 or 1. Bits are numbered sequentially starting at zero on the right sde and increasing toward the left. The bit on the left is called the most significant bit (MSB) and the bit on the right is the least significant bit (LSB). The MSB and LSB bit numbers are a 16-bit binary number. 
Binary integrers can be signed or unsigned. A signed integrer is positive or negative. An unsigned integrer is by default positive. Zero is considered positive, whereas 1 is negative. When writing don large binary numbers many people like to insert a dot every 4 or 8 bits for clarity. 

*Unsigned Binary Integers* 
Starting with the LSB, each bit in an unsigned binary integer represents an increasing power of 2. The following figure contains and 8-bit binary number. 
| 1   | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
| 2^7 | 2^6 | 2^5 | 2^4 | 2^3 | 2^2 | 2^1 | 2^0 |

*Translating unsigned binary integrers to decimal
Weighted positional notation represents a convenient way to calculate the decimal value of an unsigned binary integrer having n digits:
    dec = (Dn-1 * 2^(n-1)) + (Dn-2 *2^(n-2)) + ... + (D1 * 2^1) + (D0 * 2^(0)) 
D indicates a binary digit. 

*Translating unsigned decimal integers to binary*
To translate an unsigned decimal integer into binary, repeatedly divide the integer by 2, saving each remainder as a binary digit. We can concatenate the binary bits from the remainder column of the table in reverse order (D5, D4,...) to produce bin
