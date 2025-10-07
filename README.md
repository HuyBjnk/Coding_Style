# Coding_Style
Embedded C Coding Standard

Purpose of the Standard 
Barr Group’s Embedded C Coding Standard was designed specifically to reduce the number of programming defects in embedded software.  By following this coding standard, firmware developers not only reduce hazards to users and time spent in the debugging stage of their projects but also improve the maintainability and portability of their software.  Together these outcomes can greatly lower the cost of developing high-reliability embedded software.

## 1. General Rules
### 1.1 Which C?
- Preprocessor directive #define shall not be used to alter or rename any 
keyword or other aspect of the programming language.
- Let C be C, not some language you once loved.
### 1.2 Line Widths
- The width of all lines in a program shall be limited to a maximum of 80 
characters.
### 1.3 Braces
- Braces shall always surround the blocks of code (if, else, switch, while,...)
- Each left brace { shall appear by itself on the line below the start of the block 
it opens.  The corresponding right brace } shall appear by itself in the same 
position the appropriate number of lines later in the file. 
### 1.4 Parentheses
- To aid clarity, use parentheses (and/or break long statements into multiple lines of 
code) to ensure proper execution order within a sequence of operations.
- Unless it is a single identifier or constant, each operand of the logical AND (&&) and logical OR (||) operators shall be surrounded by parentheses.
### 1.5 Common Abbreviations
- Abbreviations and acronyms should generally be avoided unless their meanings are widely and consistently understood in the engineering community. 
- A table of project-specific abbreviations and acronyms shall be maintained in a version-controlled document.
### 1.6 Casts
- Each cast shall feature an associated comment describing how the code ensures proper behavior across the range of possible values on the right side.
Exp: result = abs((int) sample);             // WARNING: 32-bit int assumed.
### 1.7 Keywords to Avoid
Auto/Register: There is no compelling reason to use either of these keywords in modern programming practice.
Goto/Continue: Their use too often results in spaghetti code.
### 1.8 Keywords to Frequent
- Static: functions and variables that do not need to be visible outside of the module in which they are declared.
- Const: shall be used whenever appropriate (something should not be changed/modified)
- Volatile: shall be used whenever appropriate (global variable)