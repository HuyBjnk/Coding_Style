# Coding_Style
Embedded C Coding Standard

Purpose of the Standard 
Barr Group’s Embedded C Coding Standard was designed specifically to reduce the number of programming defects in embedded software.  By following this coding standard, firmware developers not only reduce hazards to users and time spent in the debugging stage of their projects but also improve the maintainability and portability of their software.  Together these outcomes can greatly lower the cost of developing high-reliability embedded software.

## I. General Rules
### 1 Which C?
- Preprocessor directive #define shall not be used to alter or rename any 
keyword or other aspect of the programming language.
- Let C be C, not some language you once loved.
### 2 Line Widths
- The width of all lines in a program shall be limited to a maximum of 80 
characters.
### 3 Braces
- Braces shall always surround the blocks of code (if, else, switch, while,...)
- Each left brace { shall appear by itself on the line below the start of the block 
it opens.  The corresponding right brace } shall appear by itself in the same 
position the appropriate number of lines later in the file. 
### 4 Parentheses
- To aid clarity, use parentheses (and/or break long statements into multiple lines of 
code) to ensure proper execution order within a sequence of operations.
- Unless it is a single identifier or constant, each operand of the logical AND (&&) and logical OR (||) operators shall be surrounded by parentheses.
### 5 Common Abbreviations
- Abbreviations and acronyms should generally be avoided unless their meanings are widely and consistently understood in the engineering community. 
- A table of project-specific abbreviations and acronyms shall be maintained in a version-controlled document.
### 6 Casts
- Each cast shall feature an associated comment describing how the code ensures proper behavior across the range of possible values on the right side.
Exp: result = abs((int) sample);             // WARNING: 32-bit int assumed.
### 7 Keywords to Avoid
Auto/Register: There is no compelling reason to use either of these keywords in modern programming practice.
Goto/Continue: Their use too often results in spaghetti code.
### 8 Keywords to Frequent
- Static: functions and variables that do not need to be visible outside of the module in which they are declared.
- Const: shall be used whenever appropriate (something should not be changed/modified)
- Volatile: shall be used whenever appropriate (global variable)

## II. Comment Rules
### 1 Acceptable Formats
- Single-line comments (//) are useful.
- Comments shall never contain the tokens /*, //, \
- Code shall never be commented out, even temporarily.
### 2 Locations and Content
- Clear and complete sentences.
- Avoid explaining the obvious, avoid writing unhelpful comment.
- All assumptions shall be spelled out in comments.
- The more complexity of the code, the more number and length of individual comment blocks.

## III. White Space Rules
### 1 Spaces
- Keywords if, while, for, switch, and return shall be followed by one space when there is
additional program text on the same line.
- Assignment operators =, +=, -=, *=, /=, %=, &=, |=, ^=, ~=, and != shall always be preceded and followed by one space.
- Binary operators +, -, *, /, %, <, <=, >, >=, ==,!=, <<, >>, &, |, ^, &&, and || shall always be preceded and followed by one space.
- Unary operators +, -, ++, --, ! , and ~, shall be written without a space on the operand side.
- Pointer operators * and & shall be written with white space on each side within declarations but otherwise without a space on the operand side.
### 2 Alignment
- Series of declarations/names of struct and union members/assignment operators within a block of adjacent assignment statements shall have their first char aligned.
- (#) shall be located at start of line.
### 3 Blank lines
- No line of code shall contain more than one statement.
- There shall be a blank line before and after each natural block of code.
### 4 Indentation
- Each level 4 characters
- A line of code too long to fit within the max line width, indent the second line when possible.
### 5 Tabs
- Never, if needed use '\t' instead.

## IV. Module Rules
### 1 Naming Conventions
- All module names shall consist entirely of lowercase letters, numbers, and underscores. No spaces shall appear within the module’s header and source file names.
- No module’s header file name shall share the name of a header file from the C Standard Library or C++ Standard Library. For example, modules shall not be named “stdio” or “math”.
- Any module containing a main() function shall have the word “main” as part of its source file name.
### 2 Header Files
- One header file for each source file and they shall always have the same root name.
- Each header file shall contain a preprocessor guard against multiple inclusion.
- The header file shall identify only the procedures, constants, and data types (via prototypes or macros, #define, and typedefs, respectively) about which it is strictly necessary for other modules to be informed.
- No public header file shall contain a #include of any private header file.
### 3 Source Files
- Each source file shall always #include the header file of the same name to allow the compiler to confirm that each public function and its prototype match.
- No source file shall #include another source file.
### 4 File Templates
- A set of templates for header files and source files shall be maintained at the project level.

## V. Data Type Rules
### 1 Naming Conventions
- The names of all new data types, including structures, unions, and enumerations, shall consist only of lowercase characters and internal underscores and end with ‘_t’.
- All new structures, unions, and enumerations shall be named via a typedef.
- The name of all public data types shall be prefixed with their module name and an underscore.
### 2 Fixed-Width Integers
8 bits          int8_t/uint8_t
16 bits         int16_t/uint16_t
32 bits         int32_t/uint32_t
64 bits         int64_t/uint64_t

- The keywords short and long shall not be used.
- Use of the keyword char shall be restricted to the declaration of and operations concerning strings.
### 3 Signed and Unsigned Integers
- None of the bitwise operators (i.e., &, |, ~, ^, <<, and >>) shall be used to manipulate signed integer data.
- Signed integers shall not be combined with unsigned integers in comparisons or expressions.  In support of this, decimal constants meant to be unsigned should be declared with a ‘u’ at the end.
### 4 Floating Point
- Avoid the use of floating point constants and variables whenever possible. Fixed-point math may be an alternative.
- Append an ‘f’ to all single-precision constants (e.g., pi = 3.141592f).
- Never test for equality or inequality of floating point values.
### 5 Structures and Unions
- Appropriate care shall be taken to prevent the compiler from inserting padding bytes within struct or union types used to communicate to or from a peripheral or over a bus or network to another processor.
- Appropriate care shall be taken to prevent the compiler from altering the intended order of the bits within bit-fields. 
### 6 Booleans
- Non-Boolean values shall be converted to Boolean via use of relational operators (e.g., < or !=), not via casts.

## VI. Procedure Rules
### 1 Naming Conventions
- No procedure shall have a name that is a keyword of any standard version of the C or C++ programming language.  Restricted names include interrupt, inline, class, true, false, public, private, friend, protected, and many others. 
- No procedure shall have a name that overlaps a function in the C Standard Library.  Examples of such names include strlen, atoi, and memset.
- No procedure shall have a name that begins with an underscore.
- No procedure name shall be longer than 31 characters.
- No function name shall contain any uppercase letters.
- No macro name shall contain any lowercase letters.
- Underscores shall be used to separate words in procedure names.
- Each procedure’s name shall be descriptive of its purpose.
- The names of all public functions shall be prefixed with their module name 
and an underscore (e.g., sensor_read()).
### 2 Functions
- A prototype shall be declared for each public function in the module header file.
- All private functions shall be declared static.
- It is a preferred practice that all functions shall have just one exit point and it shall be via a return at the bottom of the function.
- All reasonable effort shall be taken to keep the length of each function limited to one printed page, or a maximum of 100 lines.
### 3 Function-Like Macros
- Parameterized macros shall not be used if a function can be written to accomplish the same behavior.
- Surround the entire macro body with parentheses.
- Surround each use of a parameter with parentheses.
- Use each parameter no more than once, to avoid unintended side effects. 
- Never include a transfer of control (e.g., return keyword).
### 4 Threads of Execution
- All functions that encapsulate threads of execution (a.k.a., tasks, processes) shall be given names ending with “_thread” (or “_task”, “_process”).
### 5 Interrupt Service Routines
- To ensure that ISRs are not inadvertently called from other parts of the software (they may corrupt the CPU and call stack if this happens), each ISR function shall be declared static and/or be located at the end of the associated driver module as permitted by the target platform.

## VII. Variable Rules
### 1 Naming Conventions
- No variable shall have a name that is a keyword of C, C++, or any other well-known extension of the C programming language, including specifically K&R C and C99.  Restricted names include interrupt, inline, restrict, class, true, false, public, private, friend, and protected.
- No variable shall have a name that overlaps with a variable name from the C Standard Library (e.g., errno).
- No variable shall have a name that begins with an underscore.
- No variable name shall be longer than 31 characters.
- No variable name shall be shorter than 3 characters, including loop counters.
- No variable name shall contain any uppercase letters.
- No variable name shall contain any numeric value that is called out elsewhere, such as the number of elements in an array or the number of bits in the underlying type.
- Each variable’s name shall be descriptive of its purpose.
- The names of any global variables shall begin with the letter ‘g’. For example g_zero_offset. 
- The names of any pointer variables shall begin with the letter ‘p’. For example, p_led_reg.
- The names of all integer variables containing Boolean information (including 0 vs. non-zero) shall begin with the letter ‘b’ and phrased as the question they answer.  For example, b_done_yet or b_is_buffer_full.
### 2 Initialization
- All variables shall be initialized before use.
- It is preferable to define local variables as you need them, rather than all at the top of a function. 
- Any pointer variable lacking an initial address shall be initialized to NULL.

## VIII. Statement Rules
### 1 Variable Declarations
- The comma operator (,) shall not be used within variable declarations.
### 2 Conditional Statements
- It is a preferred practice that the shortest (measured in lines of code) of the if and else if clauses should be placed first.
- Assignments shall not be made within an if or else if test.
- Any if statement with an else if clause shall end with an else clause.
### 3 Switch Statements
- The break for each case shall be indented to align with the associated case, rather than with the contents of the case code block.
- Any case designed to fall through to the next shall be commented to clearly explain the absence of the corresponding break.
### 4 Loops
- Magic numbers shall not be used as the initial value or in the endpoint test of a while, do…while, or for loop.
- With the exception of the initialization of a loop counter in the first clause of a for statement and the change to the same variable in the third, no assignment shall be made in any loop’s controlling expression. 
- Each loop with an empty body shall feature a set of braces enclosing a comment to explain why nothing needs to be done until after the loop terminates.
### 5 Jumps
- The use of goto statements shall be restricted.
- C Standard Library functions abort(), exit(), setjmp(), and longjmp() shall not be used.
### 6 Equivalence Tests
- When evaluating the equality of a variable against a constant, the constant shall always be placed to the left of the equal-to operator (==).
