# *2.1 Writing a Simple Program
## **Learning Notes (Temporary)**

- boilerplate - **Boilerplate** is code that appears in many programs because it is required for the program to function correctly, even though it rarely changes.
- Here is a basic C program
  ![[Pasted image 20260707132257.png]]

- #Include studio.h , includes C standard input output library 
- Main holds the programs executable code 
- printf  is a function from the standard input/output library that can produce a formatted output 
- Return 0 ->signals to the operating system that the program finished successfully.
- \n creates a new line
- File names doesn't matter but .c is required by standard compilers
- After the program is created, we have to convert it into a form that the machine can execute using 3 steps: **Preprocessing, Compiling, Linking**
-  # commands are know as directives, the program is first given to the preprocessor which obeys commands beginning with the directive and makes modifications to the program
- Modified code goes to the compiler which translates it into machine instructions (know as object code) 
- Finally Linking combines the compiled object code with library code (like `printf`) into a single executable file.
- Commands for compiling and linking vary, but **% cc -o filename filename.c**. is usually used under Unix os
- gcc is the most popular C compiler -> **% gcc -o filename filename.c**
- IDE (Integrated Development Environments) ->  a software package that allows the editing, compiling, linking, executing, and even debugging of a program without leaving the environment.

---

## **Key Definition

printf() is a standard library function that prints formatted output to the terminal for the user.
 
 **How it Works**?
 
It is implemented inside the C Standard Library. When the program calls it, execution jumps into the library function, which writes text to standard output.
```c
printf("Hello\n");
```

---

## **Build Process / Mental Model


Source File (.c) - Where the program _is written

↓

Preprocessor  - _Handles special instructions like `#include` and makes modifications

↓

Compiler - _Converts C code into machine instructions called object code

↓

Object Code -  The translated code

↓

Linker - _Combines the compiled object code with library code (like `printf`) into a single executable file.

↓

Executable - _A complete program the operating system can run.

↓

Run - _The CPU executes the program, starting at `main().


---

## **Syntax

```c
#include <header>

int main(void)
{
    statements;

    return 0;
}
```

## **Worked Example**

```c
#include <stdio.h>

int main(void)
{
    printf("Hello, World!\n");
    return 0;
}
```

## **Explanation**s
  - _#include <stdio.h> : 
    Includes the input output library into the file

 -  int main(void):
	main() is the program's entry point. Execution begins inside main(). When main finishes, the program ends.

 -    _printf("Hello, World!\n"); :
	 printf is a  standard library function declared in the input output library <stdio.h>, that displays a formatted output in the terminal 

 - return 0; : 
	 signals to the operating system that the program finished successfully.

## **Common Mistakes**
- Forgetting the semicolon.
- Forgetting to include `<>` in stdio.h
- spelling stdio.h wrong
- Forgetting `\n` when a new line is desired.
- Forgetting quotation marks

## **Error Log**
**Error**:

![[Pasted image 20260707175328.png]]

**Cause**:
I typed studio.h (as in music), instead of the stdio.h library




# *2.2 The General Form of a Simple Program

## **Learning Notes (Temporary)**

- Every simple C program follows the same overall structure.

- A simple program consists of:
    - Directives
    - Functions
    - Statements

- Directives begin with # and are processed before compilation.
```c
#include <stdio.h>   // directive
```
- Functions are named blocks of executable code.
```c
int main(void)       // function
{
}
```
- main() is the only mandatory function because program execution begins there.

- Library functions (e.g. printf()) are provided by the C Standard Library.
```c
printf("To C, or not to C: that is the question.\n");
```
- Programmer-defined functions are written by the programmer.

- Statements perform actions while the program runs.

- Every statement ends with a semicolon.

- The return type before a function name specifies what type of value it returns.
```c
int main(void)   // returns an integer
{
    return 0;
}

```
- void inside main(void) means the function accepts no arguments.

- return 0; ends the program and reports successful execution to the operating system.

- printf() prints text exactly as written; use \n for a newline.
```c
printf("Line 1\n");
printf("Line 2\n");

```

---

## **Key Definitions

- Directives - Editing commands that modify the program prior to compilation (They always begin with #, theres no semicolon to mark the end of a directive)  
- Functions - Named blocks of executable code  
- Statements - Commands to be executed when the program runs
- function call - A statement that calls a function (e.g. library functions)
- Library function - A function provided by the C Standard Library (e.g., printf).


---

## **Build Process / Mental Model

C Program

↓

Preprocessor Directives

↓

main()

↓

Statements

↓

Function Calls

↓

return 0;

↓

Program Ends



---

## **Syntax

```c

// directives

int main()
{
 // statements 
}

```

## **Worked Example**

```c
#include <stdio.h>   // directive

int main(void)       // function
{
    printf("Hello\n");   // statement (function call)

    return 0;            // return statement
}

```

## **Explanation**s
- The data type before a function name indicates the type of value the function returns.

- Example: `nt main(void) means main returns an integer.

- void inside `mainvoid) means the function takes no arguments.

- The statement return 0; terminates the main function and indicates that it returns the value 0, signalling successful execution.

- In early C programs, you mainly use two types of statements:

- return statements
- function calls — Calling a function means asking it to perform its task.

- In pun.c, the program calls printf to display text on the screen.

- In C, every statement must end with a semicolon.

- Even though `printfis a function, using it is a function call, which counts as a statement, so it must end with a semicolon.

- printf does not automatically move to a new line after printing.

- To start a new line, you must include \n inside the string.

## **Common Mistakes**


## **Error Log






# *2.3 Comments

## **Learning Notes (Temporary)**
- The symbol /* marks the beginning of a comment and the symbol */ marks the end
- Its a sensible coding convention to Putting */ on a line by itself
```c
/* Name: pun.c 
Purpose: Prints a bad pun.
Author: K. N. King 
*/
```
- A short comment can go on the same line with other program code:
```c
int main(void) /* Beginning of main program */
```
- C99 provides a second kind of comment, which begins with // (two adjacent slashes): This style of comment ends automatically at the end of a line
```c
// This is a comment
```
## **Key Definitions

Comment: A comment in C is text inside your program that the computer ignores but humans read. It’s used to explain what the code does, who wrote it, when it was written, and why it exists.





# *2.4 Variables and Assignment

## **Learning Notes (Temporary)**
- Variables are named memory locations, Every variable must have a type (specifies what data it will hold)
- Float can store significant larger numbers than int and can store numbers with a decimal point, however arithmetic on float numbers may be slower than int. furthermore the value of a float number is often an approximation (e.g 0.1 might be 0.9997)
- Variables must be declared, first using its type then its name, if several variables have the same type their declarations can be combined
```c
int height, length, width, volume; 
float profit, loss;
```
- Declaration must proceed statements (Not in C99 tho)
```c
int main(void) 
{
	declarations
	
	statements 
}
```
- Also it is sensible coding practise to leave a blank line between declarations and statements
- A variable can be given an assignment using statements e.g.
```c
height = 8;

length = 12;

width = 10;
```

- ^ these numbers are constants
- Before a variable can be assigned a value—or used in any other way, for that matter—it must first be declared. Thus, we could write
```c
int height;

height = 8;

//but not

height = 8;

int height;

/
```
- when assigning a constant to a float variable that contains a decimal, it is best to add the letter f(for float), to avoid compiler warnings
```c
profit = 2150.48; // not this

profit = 2150.48f;// this
```
- Once a variable has been assigned a value, it can be used to help compute the value of another variable:
```c
height = 8;
length = 12; 
width = 10;
volume = height * length * width; /* volume is now 960 */
```
- printf can display the current value of a variable.
- You insert the value using a placeholder inside the string.
- %d prints an int.
- %f prints a float (default: 6 decimal places).
e.g
```c
printf("Height: %d\n", height);

// %d is a placeholder indicating where the value of height is to be filled in during printing.
```

Computing the Dimensional Weight of a Box

dimensional/Volumetric weight = volume / 166 (international shipments)
international shipments = 166
dimensional shipment = 194
height
width
length
volume
weight



## **Key Definitions

- Varibles: Variables are named memory locations
---

## **Build Process / Mental Model




---

## **Syntax

```c

int main(void) 
{
	declarations
	
	statements 
}
```

```c
%d // = interger
%f // = float
\n // newline
/ // division
%dx%dx%d // will display x after the variable
printf(" %d\n", integer);
```


## **Worked Example**

```
// DMC second rendition

  

#include <stdio.h>

  

int main(void) {

  

int height, width, length, weight, volume;

  

height = 12;

width = 10;

length = 8;

volume = (height * width * length);

weight = (volume + 165) / 166;

  

printf("Dimensions: %dx%dx%d\n", height, width, length);

printf("Volume: %d\n", volume);

printf("Weight: %d\n", weight);

  

return 0;

}

```

## **Explanation**s

- **int height, width, length, volume, weight;**
	Declares five integer variables that will store the box’s dimensions, calculated volume, and dimensional weight.


- **height = 12**
	Assigns a value to the height variable.


- **volume = height * width * length;**
	Calculates the volume of the box by multiplying its three dimensions.


- **weight = (volume + 165) / 166;**
	Calculates the dimensional weight.

	Adding **165** before dividing ensures the result is rounded **up** when using integer division.



- **printf("Dimensions: %dx%dx%d\n", ...)**
	Displays the box dimensions in a readable `12x10x8` format.


- **printf("Volume: %d\n", volume);**
	Displays the calculated volume.


- **printf("Weight: %d\n", weight);**
	Displays the calculated dimensional weight.



- **return 0;**
	Ends the program and signals successful execution to the operating system.


## **Common Mistakes**

- Choosing `float` instead of `int` when the exercise is specifically demonstrating integer arithmetic.
- Forgetting that integer division truncates decimal values.
- Forgetting to add **165** before dividing by **166**, causing the weight to round down instead of up.
- Printing dimensions without separators (e.g. `12108` instead of `12x10x8`).
- Assigning the dimensions in the wrong order (mixing up height, width, and length).
- Using the wrong format specifier (`%f` instead of `%d` for integers).
- Forgetting semicolons at the end of statements.
- Forgetting `return 0;`.

## **Error Log

1. **Used float instead of int**
![[Pasted image 20260709201755.png]]
instead
![[Pasted image 20260709201817.png]]



2. **Printed dimensions incorrectly**
![[Pasted image 20260709201942.png]]

cause
![[Pasted image 20260709202004.png]]

 
 3. **Assigned dimensions differently from the problem**
![[Pasted image 20260709202057.png]]







# *2.5 Reading Input


## **Learning Notes (Temporary)**

- Programs become much more useful when they can accept input from the user instead of relying on hard-coded values.

- scanf() is the standard library function used to read formatted input from the keyboard.

- Like printf(), the "f" in scanf stands for **formatted**.

- scanf() uses format specifiers to determine what type of data should be read.

Example:
```c
scanf("%d", &height);
```

- %d tells scanf to read an integer.

- %f tells scanf to read a float.

- The variable receiving the input must match the format specifier.

- The & operator gives scanf the memory address of the variable so it knows where to store the value.

- Every scanf() normally follows a prompt printed with printf().

Example:
```c
printf("Enter height: ");
scanf("%d", &height);
```


- Prompts usually do NOT end with \n because we want the user to type on the same line.

- After the user presses Enter, scanf() stores the input inside the specified variable.

- scanf() assumes the user enters valid input. If non-numeric data is entered when an integer is expected, the program may not behave correctly (covered later in the book).



## **Key Definitions


**scanf:** Reads formatted input from the keyboard and stores it in one or more variables.
**Format Specifier**: A placeholder that tells scanf() what type of value to read.
**Address Operator (****`&`****)**: Returns the memory address of a variable so scanf() knows where to store the input. (more in depth during pointers)

---

## **Build Process / Mental Model


Program Starts

↓

printf()

(Display prompt)

↓

User types input

↓

scanf()

(Read input)

↓

Store value inside variable

↓

Use variable in calculations

↓

Display result

---

## **Syntax

```c

int age;

scanf("%d", &age);
```

```c
float price;

scanf("%f", &price);
```

```c
printf("Enter height: ");

scanf("%d", &height);
```
## **Worked Example**

```c

#include <stdio.h>

  

int main(void) {

int height, width, length, volume, weight, divisor;

  

printf("What is the height: ");

scanf("%d", &height);

  

printf("What is the width: ");

scanf("%d", &width);

  

printf("What is the length: ");

scanf("%d", &length);

  

divisor = 166;

volume = height * width * length;

weight = (volume + (divisor - 1)) / divisor;

  

printf("Volume: %d\n", volume);

printf("Actual weight: %d\n", weight);

}
```

## **Explanation**s:

 **`printf("What is the height: ");`**

Displays a prompt asking the user to enter a value.


 **`scanf("%d", &height);`**

Reads an integer from the keyboard and stores it in the variable `height`.


 **`&height`**

Passes the memory address of `height` to `scanf()` so it knows where to store the user’s input.


**`volume = height * width * length;`**

Calculates the volume using the values entered by the user.


 **`weight = (volume + (divisor - 1)) / divisor;`**

Calculates the dimensional weight while rounding the result up using integer arithmetic.


 **`printf("Volume: %d\n", volume);`**

Displays the calculated volume.


 **`printf("Actual weight: %d\n", weight);`**

Displays the calculated dimensional weight.



## **Common Mistakes**
I would include:

- Forgetting the `&` before a variable in `scanf()`.
- Using the wrong format specifier (`%d` vs `%f`).
- Forgetting to declare the variable before reading into it.
- Using `%d` with a `float` or `%f` with an `int`.
- Printing a prompt without actually calling `scanf()`.
- Assuming `scanf()` validates user input.
- Adding `\n` to prompts (usually unnecessary).

## **Error Log

1. I wrote 
```c
scanf("%d", %length);
```
instead of
```c
scanf("%d", &length);
```


 2. **Used variables before they contained values**
output
```c
Volume: -920383360
Weight: -5544477
```
cause 
One or more variables were never assigned because `scanf()` was missing or incorrect.

lesson
Always make sure every variable has been assigned a value before using it in calculations.






# *2.6 Defining Names for Constants


## **Learning Notes (Temporary)**

- it is useful to name constants, we can do this using a feature called macro definition 
-  # define is another preprocessing directive, which replaces each macro by the value it represents e.g.
```c
#define INCHES_PER_POUND 166
weight = (volume + INCHES_PER_POUND - 1) / INCHES_PER_POUND;

// will become

weight = (volume + 166 - 1) / 166;
```

- the value of a macro can be an expression (using brackets if it contains an operator) e.g.
```c
#define RECIPROCAL_OF_PI (1.0f / 3.14159f)
```
- it is C coding Convention to use uppercase for macro names, not a requirement
- A **macro** is simply a name that represents another piece of text.
- Macro replacement happens **before compilation**, during preprocessing.- 
## **Key Definitions

 **Macro Definition**:A preprocessing directive that defines a name to represent a constant or expression.


 **Macro**:A named constant or expression that the preprocessor replaces before compilation.


 **Constant**:A fixed value that does not change while the program runs.


 **Identifier**:A programmer-defined name used for variables, functions, macros, and other program elements.

---

## **Build Process / Mental Model


Source Code

↓

#define creates macro names

↓

Preprocessor replaces each macro
with its value

↓

Compiler compiles the modified code

↓

Executable runs normally


---

## **Syntax


```
#define NAME value


```

```c
#define INCHES_PER_POUND 166
```

```c
#define SCALE_FACTOR (5.0f / 9.0f)
```
## **Worked Example**

```c
#include <stdio.h>

#define FREEZING_PT 32.0f
#define SCALE_FACTOR (5.0f / 9.0f)

int main(void)
{
    float fahrenheit, celsius;

    printf("Enter Fahrenheit: ");
    scanf("%f", &fahrenheit);

    celsius = (fahrenheit - FREEZING_PT) * SCALE_FACTOR;

    printf("Celsius: %.1f\n", celsius);

    return 0;
}

```

## **Explanation**s:

 



## **Common Mistakes**

- Forgetting that `#define` is a preprocessing directive (no semicolon).
- Using lowercase names for macros (against common C convention).
- Forgetting parentheses around macro expressions.
- Using magic numbers instead of named constants.
- Assuming macros are variables (they are simply text replacements).
- Using integer arithmetic (`5 / 9`) instead of floating-point arithmetic (`5.0f / 9.0f`).
## **Error Log
1. Used integer division in a macro
 wrong
 ```c
 #define SCALE_FACTOR (5 / 9)
 ```
 result
 ```c
 SCALE_FACTOR becomes 0
 ```
 correct
 ```c
 #define SCALE_FACTOR (5.0f / 9.0f)
 ```






# * 2.7 Identifiers

 
## **Learning Notes (Temporary)**

- identifiers are names for variables, functions, macros and other elements 
- They must start with a letter or underscore and can contain letters, digits, or underscores As C is case sensitive
- Coding convention, is lower case for identifiers using an upper-case letter to begin each word within an identifier: e.g. currentPage
- Keywords cant be used as identifiers
![[Pasted image 20260714210825.png]]
- C is case‑sensitive, so all keywords and standard library function names must be written exactly in lowercase.

## **Key Definitions
identifiers: names for variables, functions, macros and other elements 



---

## **Build Process / Mental Model



---

## **Syntax

```c

```

```c

```

```c

```
## **Worked Example**

```c


```

## **Explanation**s:

 



## **Common Mistakes**


## **Error Log





# *2.8 Layout of a C Program


## **Learning Notes (Temporary)**

- A C program is made up of **tokens**, which are the smallest meaningful units of the language.
- Common token types include:
**Identifiers** (e.g., zprintf, height)
**Keywords**
**Operators** (e.g., +, -)
**Punctuation** (e.g.,, ;, (,))
**String** literals (e.g., "Height: %d\n")

- The  statement
```c
printf("Height: %d\n", height);
```
contains **seven tokens** : 
printf
 (
  "Height: %d\n"
  ,
   height
   ) 
   ;
   - The spacing between tokens usually doesn’t matter; tokens can be placed right next to each other as long as doing so doesn’t accidentally form a different token.
e.g.
```c
/* Converts a Fahrenheit temperature to Celsius */ #include <stdio.h> #define FREEZING_PT 32.0f #define SCALE_FACTOR (5.0f/9.0f) int main(void){float fahrenheit,celsius;printf( "Enter Fahrenheit temperature: ");scanf("%f", &fahrenheit); celsius=(fahrenheit-FREEZING_PT)*SCALE_FACTOR; printf("Celsius equivalent: %.1f\n", celsius);return 0;}
```
- You could compress code into very few lines, but preprocessing directives must each stay on their own line.

- Over‑compressing code is discouraged; adding spaces and blank lines improves readability, and C freely allows whitespace between tokens.
- C allows unlimited whitespace (spaces, tabs, newlines) between tokens, enabling statements to span multiple lines.
- Adding spaces around operators and after commas improves readability and helps visually separate tokens.
- Indentation makes nested code structures clearer, especially inside functions like main.
- Blank lines help divide a program into logical sections, making structure easier to understand.
- Braces { and } placed on their own aligned lines make function boundaries easy to spot and simplify adding/removing statements.

- Whitespace cannot be inserted inside a token (e.g., fl oat) without causing errors; splitting string literals across lines is also illegal without special syntax.
## **Key Definitions




---

## **Build Process / Mental Model



---

## **Syntax

```c

```

```c

```

```c

```
## **Worked Example**

```c


```

## **Explanation**s:

 



## **Common Mistakes**


## **Error Log
