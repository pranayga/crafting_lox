# Interpreters 101
Basic steps in interpreters

## Basic Steps

### Scanning
- Lexing or scanning
- Basically taking in the text and tokenizing

### Parsing
- Creating a parse/abstract-syntax tree from the token
- humans are shitty in their language, especially with the sarcasm

### Static analysis
- Now that we have an AST, what all can we do on it?
    - We can do static analysis
    - all the analysis and optimizations
    - all the compile time error which are not syntax related
    - cool stuff

### Intermediate Representations
- Some middle land, 
    - could be a machine independent assembly
    - could be object code
- Front end: lan -> IR
- Back end: IR -> native bytecode

### Optimization
- Well maybe optimization isn't part of static anaylsis

### Code Generation
- The actual backend
- Generating machinecode form the IR
- Well maybe not machine code
    - P-code (portable code instead)
    - Truns out instead of going from IR to x86, we have more indirections
    - I am confused now, does have produces object code (IR) or bytecode?
    - is bytecode the p-code and IR code something purely internal to 
    the compiler/interpreter?

### Virtual Machine
- Well bytecode required a VM since no machine talks bytecode. So I guess,
java is bytecode.
- We can now write a compiler for each byte-code to native language
    - So the stack looks something like code -> AST -> IR -> Bytecode -> MachineCode

### Runtime
- Memory Management, gargae collection etc 
- This is the stuff we will need while we are running out Virtual Machine?!
- Depending on the type:
    - Compiled languages, it's instrumented into the codebase
    - for VM (interpret) one, it lives in the VM

## Shortcuts & Alt Routes

### Single-pass Compilers
- interleave parsing, and code gen
    - Produces output code directly
        - may not require to gen a AST
        - nat bit generate any  IRs
    - You see some code, you know how the machine code for it will look like
- Pascal and C was designed arount this area
- That's why you need forward declaration, which makes sense IMO

### Transpilers
Writing your own IR to machinecode generation is hard. Having 
so many platforms don't help. 
But of well, maybe that's too much work. So what if you could 
convert your language's code into some other language? Like a front-end
that converts your code into another language?!
- this is source-to-sourcer or transpiler
- lot of langauges have transpilers, mostly all languages do
- you can also so a lot of optimizations steps to produce simpler or
more optimzable target source!

### JIT
Compile to target in real time on the target's machine. JVM, CLR,
V8, all does this! It's a pain though.

"The most sophisticated JITs insert profiling hooks into the generated
code to see which regions are most performance critical and what kind
of data is flowing through them. Then, over time, they will
automatically recompile those hot spots with more advanced optimizations."

Yeah, sounds about right.

## Compilers VS interpreters
It's as different as fruits and vegetables. As in, it's confusing :D

### Compiling:
- involves translating source to some lower level form (machine code
or bytecode), transpiling could also be termed as compiling
- The compiler usually only does the compilation but no exec
- takes source and exec it immediately

- Cpython like V8 may have both goin on inside.

