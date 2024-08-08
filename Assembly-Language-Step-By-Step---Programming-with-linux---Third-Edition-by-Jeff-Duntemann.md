# Assembly Language Step by Step
## Programming with Linux

# Contents at a Glance

# Chapter 1 - Another Pleasant Valley Saturday - Understanding waht Computers Really Do.
... 


*Assembly Language Programming as a Board Game*
- Take a look a figure 1-2. It is a fair approximation of assembly language as it was used on some of the simplier computers years ago. The column marked "programming instructions" is the main path around the edge of the board, of which only a portion can be shown here. This is the assembly language computer program, the actual series of steps and tests that, when executed, cause the computer to do something. Setting up this series of program instructions is what programming in assembly language actually is. 
- Everything else is odds and ends in the middle of the board that serve the game in progress. Most of these are storage locations that contain your data. You've probably noticing that there are a lot of numbers involved. Assembly at its innermost level, is nothing but numbers, and if you hate numbers you will have a rought time of it. Higher level programming languages such as Pascal or Python disguise the numbers by treating them symbolically, but assemblyanguage language, its just you and the numbers. 
- Figure 1-2: the game of assembly language. 
  
*Code and Data* 
- like most board games, the assembly language board game consists of two broad categories of elements; game steps and places to store things. The "Game steps" are the steps and tests that have been spoken of. The places to store things, are just that: cubbyholes into which you can place numbers, with the confidence that those numbers will remain where you put them until you take them out or change them somehow.
- In programming terms, the game steps are called code, and the numbers in their cubbyholes are called data. The cubbyholes themselves are usually called storage (This difference, between the places you store information and the information you store in them is crucial). 
- Recall, the Game of Big Bux, as it works the same. In the start a Business detour, there is an instruction reading "add 850,000 dollars to checking account." The checking account is one of several different kinds of storage in the Game of Big Bux, and money values are a type of data. Its no different conceptually from an instructio in the Game of Assembly reading add 5 to register A. An ADD instruction in the code alters a data value stored in a cubbyhole named register A. 
- Code and data are two very different kinds of critters, but they interact in ways that make the game interesting. The code includes steps that place data into storage (MOVE instructions) and steps that alter data that is already in storage (INCREMENT and DECREMENT instructions, and ADD instructions). 
