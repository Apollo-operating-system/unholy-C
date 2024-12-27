# Introduction

This document provides information about Unholy C, a programming language that combines elements of C, assembly, C65 BASIC, and LaTeX for mathematical operations. It includes guidelines on syntax, control flow, function definitions, and other essential features for effective coding in Unholy C. The table of contents below outlines the structure of the document and the key topics covered.



```
10 main
20 int x = 1
30 int target = 5
40 print "Starting program with target: " target
50 goto incrementFunction

A10 incrementFunction /M
A20 print "In incrementFunction: x = " x
A30 x = x + 1
A40 if x >= target goto checkFunction
A50 if x < target goto displayFunction

B10 checkFunction /C
B20 print "In checkFunction: Checking x = " x
B30 if x >= target goto endFunction
B40 goto incrementFunction

1A10 displayFunction /C /S1
1A20 print "In displayFunction: Displaying x = " x
1A30 if x == 2 goto checkFunction
1A40 x = x + 1
1A50 if x == 3 goto endFunction
1A60 goto incrementFunction

1B10 endFunction /C
1B20 print "In endFunction: Ending program"
1B30 END /VM
```


# Line Number Prefixes

In Unholy C, line numbers use a prefixing system to differentiate between the main function and other functions:

 Main Function

- **Line Numbers:** 10, 20, 30, ..., 40

 Function 1 (A Prefix)

- **Line Numbers:** A10, A20, A30, ..., A40

 Function 2 (B Prefix)

- **Line Numbers:** B10, B20, B30, ..., B40

This pattern continues up to function 26 (Z prefix). For functions beyond 26, prefixes loop back with additional letters:

 Extended Functions

- **Function 27:** AA10, AA20, ..., AA40
- **Function 28:** BA10, BA20, ..., BA40

The pattern follows a systematic approach, ensuring each function has a unique line number prefix, making the code easier to read and maintain.

## Scope Reset

To reset the prefix, use a scope reset tag. After a scope reset, functions are called with an additional numerical prefix:

**Example:** The first function after the reset is called 1A instead of A.

## Tags

### Function Tags

- **/C** Unholy C Code functions  
  **Extra Info:** Standard C-style functions for general-purpose programming.  
  **Non-Compatibility:** /A, /M

- **/A** X86_64 Assembly functions  
  **Extra Info:** Functions written in x86_64 assembly language. I/O keywords are still valid.  
  **Non-Compatibility:** /C, /M

- **/M** LaTeX Math functions  
  **Extra Info:** Functions for mathematical expressions and calculations, formatted in LaTeX. I/O keywords are still valid.  
  **Non-Compatibility:** /C, /A

### Scope Reset

- **/S[number]** Starts a new scope  
  **Extra Info:** Resets the line number prefix for subsequent functions until the next scope is defined. Useful for organizing code into modular sections.  
  **Non-Compatibility:** None

## Performance Optimization

- **/OS** Optimize for Speed  
  **Extra Info:** Prioritizes execution speed over other factors.  
  **Non-Compatibility:** /OM

- **/OM** Optimize for Memory  
  **Extra Info:** Minimizes memory usage, potentially at the expense of speed.  
  **Non-Compatibility:** /OS

- **/IN** Inline method  
  **Extra Info:** Encourages the compiler to inline the function for faster execution.  
  **Non-Compatibility:** /NI

- **/NI** No inline  
  **Extra Info:** Prevents the compiler from inlining the function, useful for debugging.  
  **Non-Compatibility:** /IN

- **/HS** Hot Spot  
  **Extra Info:** Marks a function as a performance-critical section to prioritize optimizations.  
  **Non-Compatibility:** None

## Debugging and Logging

- **/LE** Log Execution  
  **Extra Info:** Enables detailed logging of function execution for debugging purposes.  
  **Non-Compatibility:** /NL

- **/NL** No Log  
  **Extra Info:** Disables logging for this function to reduce overhead.  
  **Non-Compatibility:** /LE

- **/DB** Debug  
  **Extra Info:** Enables debug mode, which includes additional checks and verbose output.  
  **Non-Compatibility:** None

## Security

- **/SC** Secure  
  **Extra Info:** Implements security features to prevent vulnerabilities.  
  **Non-Compatibility:** /SB

- **/SB** Sandbox  
  **Extra Info:** Runs the function in a restricted environment to contain potential issues.  
  **Non-Compatibility:** /SC

## Garbage Collection

- **/CS** Critical Section  
  **Extra Info:** Marks code that should not be interrupted by garbage collection.  
  **Non-Compatibility:** None

- **/LL** Low Latency GC  
  **Extra Info:** Ensures that garbage collection is performed with minimal impact on performance.  
  **Non-Compatibility:** None

## Concurrency

- **/TS** Thread Safe  
  **Extra Info:** Ensures that the function can be safely called from multiple threads.  
  **Non-Compatibility:** /ST

- **/ST** Single Threaded  
  **Extra Info:** Indicates that the function should only be called from a single thread.  
  **Non-Compatibility:** /TS

- **/CC** concurrent
- **Extra Info:** Allows the function to run concurrently with others, handling synchronization internally.
- **Non-Compatibility:** None

## Resource Management

- **/MI** Memory Intensive 
- **Extra Info:** Indicates that the function uses a significant amount of memory.
- **Non-Compatibility:** None

- **/RI** Resource Intensive 
- **Extra Info:** Indicates that the function heavily uses system resources, such as CPU or I/O.
- **Non-Compatibility:** None

## Deprecated and Compatibility

- **/DP** Deprecated
- **Extra Info:** Marks a function as deprecated and suggests it should not be used in new code.
- **Non-Compatibility:** None

- **/BC** Backward Compatible
- **Extra Info:** Ensures the function maintains compatibility with older versions of the compiler.
- **Non-Compatibility:** None


# Syntax Rules

## Line Structure

Each line begins with a line number, followed by the statement or command.

**Example:**

```
10 int x = 1
20 print "Hello, World!"
```

## Comments

Lines without line numbers are treated as comments.

**Example:**

```
This is a comment
10 int x = 1
Another comment
20 print "Hello, World!"
```

## Special Characters

- **String Literals:** Enclosed in double quotes (").

  **Example:**

  ```
  20 print "This is a string literal"
  ```

- **Assignment Operator (=):** Used to assign values to variables.

  **Example:**

  ```
  30 x = x + 1
  ```

- **Arithmetic Operators:** +, -, *, /.

  **Example:**

  ```
  40 y = x * 2
  ```

- **Comparison Operators:** ==, !=, <, >, <=, >=.

  **Example:**

  ```
  50 if x >= target goto B
  ```

- **Logical Operators:** && (and), || (or), ! (not).

  **Example:**

  ```
  60 if (x > 0 && y < 10) goto C
  ```

- **Colon (:):** Used for defining labels.

  **Example:**

  ```
  20 loop_start:
  30 x = x + 1
  40 if x < 10 goto loop_start
  ```

- **Goto Keyword:** Jumps to specific labels or functions.

  **Example:**

  ```
  50 goto A
  ```

- **Forward Slash (/):** Used in function tags, attributes, and compilation targets.

  **Example:**

  ```
  A10 incrementFunction /M
  ```

- **Square Brackets ([]):** Used to denote embedded function tags.

  **Example:**

  ```
  10 AMCStart [ASM]
  20 mov rax, 10
  30 mov rbx, 20
  40 add rax, rbx
  50 AMCEnd [ASM]
  ```

---

## Control Flow

### If Statements

Conditional execution uses `if` followed by a condition and `goto` for branching.

**Syntax:** `if [condition] goto [label]`

**Example:**

```
40 if x >= target goto B
```

### Loops

Created using labels and `goto` for iteration.

**Example:**

```
10 int x = 0
20 loop_start:
30 x = x + 1
40 if x < 10 goto loop_start
50 print "Loop finished"
```

---

## Function Definitions

Functions are prefixed with a line number and a function tag to define their type.

**Example:**

```
A10 incrementFunction /M
A20 x = x + 1
A30 if x < target goto A20
A40 goto main
```

### Embedded Function Tags

You can embed other function types within a function using the following syntax:

**Example:**

```
10 AMCStart [ASM/MATH/CODE]
20 mov rax, 10
30 mov rbx, 20
40 add rax, rbx
50 AMCEnd [ASM/MATH/CODE]
```

---

## Compilation Targets

Unholy C can compile into bytecode (similar to Java) or target specific architectures. The compilation target is determined by the last line in the code:

```
/VM: Compile for bytecode virtual machine.
```
```
/X86_64: Compile into X86_64 assembly.
```

If no compilation target is specified, the default is VM bytecode.

---

## Modules and Includes

External libraries and modules can be included before the main function using the following directives:

- module
- import
- export
- package

**Example:**

```
import file_name.uc
10 mainFunction /C
20 main
30 print "Hello, World!"
```

---

## Standard Libraries

Standard libraries will be added in future versions.

---

## 26-Instruction Bytecode 

## Instruction Format
```
[6 bits: Opcode][4 bits: Operation Mode][6 bits: Sub-operation][8 bits: Flags][8 bits: Extended Flags]
```

## Core Memory Operations (6 instructions)
1. `MEM` - Universal Memory Operation
   - Primary ops (via mode):
     - Load/Store (normal memory)
     - Atomic operations (CAS, fetch-modify)
     - Volatile access
   - Flags control:
     - Alignment requirements
     - Memory barriers (mb, rmb, wmb)
     - Cache operations
     - Segment:offset addressing

2. `STACK` - Stack/Frame Management
   - Primary ops:
     - Push/Pop
     - Frame creation/destruction
     - Exception frame management
     - Try/catch block setup
   - Flags control:
     - Stack unwinding
     - Exception handling state
     - Frame type (normal/exception/interrupt)

3. `PORT` - I/O and Synchronization
   - Primary ops:
     - I/O operations (in/out)
     - Mutex operations
     - Thread synchronization
   - Flags control:
     - Port access type
     - Synchronization primitive type
     - Privilege level

4. `ALLOC` - Memory Management
   - Primary ops:
     - Allocation/Deallocation
     - Object creation/destruction
     - Array management
   - Flags control:
     - Alignment requirements
     - Object lifecycle
     - Constructor/destructor chaining

5. `FIELD` - Structure Access
   - Primary ops:
     - Member access
     - Virtual table management
     - Interface dispatch
   - Flags control:
     - Access type (direct/virtual)
     - Multiple inheritance resolution
     - Field alignment

6. `ATOMIC` - Atomic Operations
   - Primary ops:
     - Compare-and-swap
     - Fetch-and-modify
     - Memory fences
   - Flags control:
     - Operation type
     - Memory ordering
     - Barrier requirements

## Control Flow (6 instructions)
7. `FLOW` - Basic Control
   - Primary ops:
     - Conditional/unconditional jumps
     - Switch/case handling
     - Loop control
   - Flags control:
     - Condition type
     - Flow type
     - Branch prediction hints

8. `CALL` - Function Management
   - Primary ops:
     - Function calls
     - Method dispatch
     - Syscall/interrupt handling
   - Flags control:
     - Call type (direct/virtual/interrupt)
     - Privilege transitions
     - Parameter passing method

9. `RET` - Return Control
   - Primary ops:
     - Function return
     - Exception return
     - Interrupt return
   - Flags control:
     - Return type
     - Stack cleanup
     - Privilege restoration

10. `EXC` - Exception Control
    - Primary ops:
      - Try/catch handling
      - Exception throwing
      - Finally block management
    - Flags control:
      - Exception type
      - Handler selection
      - Cleanup actions

11. `ISR` - Interrupt/Signal
    - Primary ops:
      - Interrupt handling
      - Signal processing
      - Hardware events
    - Flags control:
      - Priority levels
      - Interrupt masking
      - Hardware interface

12. `SYNC` - Synchronization Control
    - Primary ops:
      - Thread sync
      - Lock management
      - Barrier control
    - Flags control:
      - Sync primitive type
      - Wait conditions
      - Timeout handling

## Data Operations (6 instructions)
13. `ALU` - Arithmetic/Logic
    - Primary ops:
      - Math operations
      - Bitwise operations
      - Type conversions
    - Flags control:
      - Operation type
      - Data type
      - Precision control

14. `CMP` - Universal Compare
    - Primary ops:
      - Value comparison
      - Object comparison
      - Type checking
    - Flags control:
      - Comparison type
      - Type information
      - Equality semantics

15. `CONV` - Type Management
    - Primary ops:
      - Type conversion
      - Generic resolution
      - Type checking
    - Flags control:
      - Source/target types
      - Conversion rules
      - Generic parameters

16. `STR` - String/Array
    - Primary ops:
      - String operations
      - Array operations
      - Collection management
    - Flags control:
      - Operation type
      - Element type
      - Boundary checking

17. `BIT` - Bit Manipulation
    - Primary ops:
      - Bitfield operations
      - Bit patterns
      - Flags management
    - Flags control:
      - Field width
      - Bit patterns
      - Endianness

18. `VEC` - Vector Operations
    - Primary ops:
      - SIMD operations
      - Bulk data movement
      - Parallel processing
    - Flags control:
      - Vector width
      - Operation type
      - Element type

## Object System (4 instructions)
19. `OBJ` - Object Control
    - Primary ops:
      - Object lifecycle
      - Virtual dispatch
      - Interface management
    - Flags control:
      - Object type
      - Inheritance chain
      - Interface mapping

20. `VTBL` - Virtual Table
    - Primary ops:
      - Virtual table management
      - Method resolution
      - Interface dispatch
    - Flags control:
      - Table type
      - Resolution strategy
      - Inheritance depth

21. `META` - Metadata
    - Primary ops:
      - Type information
      - Attributes
      - Reflection
    - Flags control:
      - Information type
      - Attribute processing
      - Reflection depth

22. `DBG` - Debug/Development
    - Primary ops:
      - Debug operations
      - Assertions
      - Tracing
    - Flags control:
      - Debug level
      - Trace type
      - Assert handling

## No Operations (2 instructions)
23. `NOP1` - No Operation 1
    - Can be used for alignment
    - Pipeline control
    - Timing adjustments

24. `NOP2` - No Operation 2
    - Can be used for alignment
    - Pipeline control
    - Timing adjustments

## Special Purpose (2 instructions)
25. `SYS` - System Management
    - Primary ops:
      - System calls
      - Privilege management
      - Resource control
    - Flags control:
      - System operation
      - Resource type
      - Privilege level

26. `EXT` - Extended Operations
    - Primary ops:
      - Complex operations
      - Custom handlers
      - Special cases
    - Flags control:
      - Operation selection
      - Handler type
      - Custom parameters


# Keywords

## Types
- char
- int
- float
- double
- void
- long
- unsigned
- volatile
- alignas
- alignof
- sizeof
- atomic
- packed
- string
- array
- boolean

## Memory Model Keywords
- virtual
- physical
- port
- segment
- offset

## Object-Oriented Features
- interface
- implements
- abstract
- final
- override
- super

## Privilege and Protection
- kernel
- user
- interrupt
- syscall
- privileged

## Control Flow
- if
- else
- for
- while
- do
- switch
- case
- break
- continue
- return
- default
- goto
- isr
- foreach
- until
- select
- try
- catch
- finally

## Storage and Type Modifiers
- static
- const
- extern
- inline
- restrict
- naked
- noreturn
- readonly
- shared
- volatile
- transient

## Data Structures
- struct
- union
- enum
- typedef
- bitfield
- collection
- list
- queue
- stack

## Debug and Development
- debug
- assert
- print
- trace
- benchmark

## Special Purpose Keywords
- _Atomic
- _Generic
- asm
- barrier
- synchronized

## Attributes
- section
- aligned
- weak
- export
- deprecated
- unsafe
- optimize

# Memory Operations
## I/O Operations
- in
- out
- io_read
- io_write

## Memory Barriers
- mb
- rmb
- wmb

## Cache Operations
- cache_flush
- cache_invalidate
- prefetch

## Error Handling
- throw
- throws
- error

# Essential Preprocessor Directives
- if
- elif
- else
- endif
- ifdef
- ifndef
- define
- undef
- include
- pragma
- error
- region
- link_section

# Quality of Life Features

## String Operations
- concat
- split
- format

## Documentation
- doc
- summary
- param
- returns

## Module System
- module
- import
- export
- package