# C Language Quick Start Guide

## 1. Variables: Naming Memory "Rooms"

### Analogy

A computer's memory is like an infinitely large "digital building." The smallest storage unit is a "1-square-meter room" (1 byte), and each room has a unique "doorplate number" (memory address, such as a hexadecimal number like `0x7ffeefbff5c4`).

- **Declaring a variable**: Telling the computer, "I want to occupy this/these room(s) and give it a name."
- **Variable type**: The "layout" of the room—different layouts can hold different things (e.g., `char` is a 1-square-meter studio that can only hold one character; `int` is a 4-square-meter large room that can hold integers; `float` is a room with刻度 (scale) that can hold decimals).
- **Assignment**: Putting something into the room.
- **Variable name**: A "nickname" for the room (e.g., using `temp` for temperature is 100 times easier to remember than directly memorizing the doorplate number `0x7ffeefbff5c4`).

### Example

```c
#include <stdio.h>  // Input/output header file needed for general C programs

int main() {
    // Declare variables of different types (occupying rooms of different layouts)
    char gender;       // 1-byte room, stores gender ('M'=male, 'F'=female)
    int age;           // 4-byte room, stores age (e.g., 25 years old)
    float height;      // 4-byte room with scale, stores height (e.g., 175.5cm)

    // Assignment: Putting things into the rooms
    gender = 'M';
    age = 25;
    height = 175.5f;  // Note: adding 'f' for float assignment

    // Print variables (checking what's in the rooms)
    printf("Gender: %c\n", gender);
    printf("Age: %d\n", age);
    printf("Height: %.1fcm\n", height);
    return 0;
}
```

### Key Points to Note

- Variable names should be meaningful (don't use a/b/c), like `user_age`, `product_price`.
- The type must be specified when declaring a variable so the computer knows how large a "room" to allocate.

#### Tip:

> For a C program,
> 
> ```c
> #include <stdio.h>
> ```
> 
> means "this program needs the header file called stdio.h."
> 
> `stdio` stands for "standard input/output." After all, the programs we write definitely need input and output, so we'll just include this header file by default from now on.
> 
> ```c
> int main() {
> 
> }
> ```
> 
> This is the main function of a C program, the "entry point" of the program. It means the program starts execution from the main function. We'll mention the main function again when we talk about functions.

## 2. Conditionals & Loops: Making the Program "Make Choices and Repeat"

If variables are "rooms," then conditionals and loops are the "butler"—the butler decides "what to do" and "how many times to repeat something" based on rules.

### 2.1 Conditionals (if/else): The Butler Makes Choices

#### Analogy

It's like "if it rains, take an umbrella; otherwise, take a hat"—the butler performs different operations based on a "condition."

- Condition: e.g., "is the number in the room greater than 18?" (`age > 18`)
- Execution: If the condition is true, take the `if` branch; if false, take the `else` branch.

#### Example (Checking if Adult)

```c
#include <stdio.h>

int main() {
    int age = 20;  // Define age variable
    char is_adult = 0;  // 0=minor, 1=adult

    // Check: Age >= 18 means adult
    if (age >= 18) {
        is_adult = 1;
        printf("Age: %d, Adult\n", age);
    } else {
        is_adult = 0;
        printf("Age: %d, Minor\n", age);
    }
    return 0;
}
```

We just need to understand:

```c
if(condition) {
    Thing to do when condition is true;
}
else {
    Thing to do when condition is false;
}
```

```c
if(condition1) {
    Thing to do when condition1 is true;
}
else if(condition2) {
    Thing to do when condition1 is false (because if condition1 was true, the thing above was already done) AND condition2 is true;
}
else {
    Thing to do when none are true;
}
```

#### A Little Aside:

> **C language is not sensitive to line breaks and alignment in code.**
> 
> That is:
> 
> ```c
> if (age >= 18) {
>     is_adult = 1;
>     printf("Age: %d, Adult\n", age);
> } else {
>     is_adult = 0;
>     printf("Age: %d, Minor\n", age);
> }
> ```
> 
> and
> 
> ```c
> if (age >= 18) {
> is_adult = 1;printf("Age: %d, Adult\n", age);
> } else {
>     is_adult = 0;
> printf("Age: %d, Minor\n", age);}
> ```
> 
> or even
> 
> ```c
> if(age>=18){is_adult=1;printf("Age: %d, Adult\n",age);}else{is_adult=0;printf("Age: %d, Minor\n",age);}
> ```
> 
> All three will produce the same running result.
> 
> But for code readability, please be sure to follow the standard when writing code, don't write messily:
> 
> > Indent inside curly braces by 4 spaces (must)
> > 
> > Add spaces around operators (+ - * / & % ! = < > <= >= ==)
> > 
> > If there is a comma or semicolon on the same line, add a space after it

### 2.2 Loops (for/while): The Butler Repeats Tasks

#### Analogy

- **for loop**: "Do something a definite N times"—e.g., "put numbers 1-10 into 10 rooms one by one."
- **while loop**: "Do something as long as a condition is true"
  e.g., "as long as balance > 0, deduct 10 yuan each time until balance is 0."

#### Example 1: for Loop (Batch Assignment + Printing)

```c
#include <stdio.h>

int main() {
    // Loop 5 times, print numbers 1-5
    for (int i = 0; i < 5; i++) {  // i goes from 0 to 4, total 5 times
        printf("Current count: %d\n", i);
    }

    // Loop to assign values to an array (multiple consecutive rooms)
    int scores[5];  // 5 int rooms, store 5 scores
    for (int j = 0; j < 5; j++) {
        scores[j] = 80 + j * 2;  // Assign 80, 82, 84, 86, 88
        printf("Score %d: %d\n", j+1, scores[j]);
    }
    return 0;
}
```

#### Example 2: while Loop (Continuous Deduction)

```c
#include <stdio.h>

int main() {
    int balance = 35;  // Initial balance 35 yuan

    // As long as balance > 0, deduct 10 yuan each time
    while (balance > 0) {
        printf("Current balance: %d yuan, deducting 10 yuan\n", balance);
        balance -= 10;  // Balance minus 10
    }
    printf("Balance is now 0, stopping deduction\n");
    return 0;
}
```

### Key Points to Note

- Loops must have an "exit condition," otherwise they become an "infinite loop" (e.g., `while(1)` will make the program run forever, use with caution).
- The for loop is suitable for scenarios where "the number of loops is known," while the while loop is suitable for scenarios where "the number of loops is unknown, only the termination condition is known."

## 3. Functions: Giving a "Set of Operations" a Name

The essence of functions in C language is completely consistent with the logic of functions in high school mathematics—in math we learned `f(x) = 2x + 1`, giving the independent variable `x` a value allows us to calculate a unique result through a fixed rule. C language functions encapsulate "code operations" into a similar "mathematical function rule," passing it an "independent variable (parameter)," and it executes according to preset logic and returns a "function value (return value)."

- **Function definition**: Corresponds to "defining the function expression" in mathematics (e.g., explicitly stating the rule `f(x) = 2x + 1`), writing clearly the operations the C function will perform, the needed "independent variables" (parameters), and the returned "function value" (return value).

- **Function call**: Corresponds to "substituting x to find the value" in mathematics (e.g., calculating `f(3)`). Calling a C function means passing values to the parameters, letting the function execute its preset operations.

- **Parameters**: Correspond to the "independent variables" of a mathematical function (e.g., `x` in `f(x)`, `x` and `y` in `f(x,y)=x+y`). They are the "input values" needed for the function to execute.

- **Return value**: Corresponds to the "function value" of a mathematical function (e.g., `7` in `f(3)=7`). It is the "result value" output after the function finishes executing.
  For a more relatable example:
  In math, defining `S(a,b) = a + b` (finding the sum of two numbers), calculating `S(10,25)` gives 35.
  In C, defining `add(int a, int b)` (finding the sum of two numbers), calling `add(10,25)` also gives 35—both follow the logic of "define rule → pass values → get result."

### Example

```c
#include <stdio.h>

// Function definition: Corresponds to defining S(a,b) = a + b in math
// Parameters a, b: Correspond to the independent variables of the math function. Return value: Corresponds to the math function value (int type)
int add(int a, int b) {
    int result = a + b; // Corresponds to the calculation rule a+b in math
    return result; // Return the function value, corresponds to the result of S(a,b) in math
}


// Function definition: A function with no return value (similar to an operation in math that "only executes a rule, doesn't evaluate")
// void means no return value, like in math only performing "print the values of a and b," not calculating a result
void print_info(char name[], int age) {
    printf("Name: %s, Age: %d\n", name, age);
}

int main() {

    // Function call: Corresponds to calculating S(10,25) in math, assigning the result to sum
    int sum = add(10, 25);
    printf("Result of 10+25: %d\n", sum); // Output sum, i.e., S(10,25)=35

    // Function call: Pass the two "independent variables" "Zhang San" and "25", execute the print operation
    print_info("Zhang San", 25);
    print_info("Li Si", 30);
    return 0;
}
```

### Key Points to Note

- `main()` is the "main function"—analogous to the "total operation entry" in math: all calculations in a math problem start from the "master formula." A C program always starts execution from `main()`. Other functions (like `add`, `print_info`) must be called by `main()` (like substituting into the master formula for calculation) to run.

- Function parameters must match the types in the definition: Just like `f(x)` in math might require `x` to be an integer, you can't substitute a string. In C, `print_info` requires a character array (name) for the first parameter, so you can't pass a number.

- `void` type functions have no return value: Like some operations in math that only execute (e.g., "draw a coordinate system") and don't produce a specific numerical result. Such functions don't need to write `return result;`, only `return;` (or it can be omitted).

## 4. Pointers: Directly Operating on "Room Doorplate Numbers"

Pointers are the "core super move" of C language, slightly harder for beginners to grasp—mastering pointers allows direct control of memory, making programs more flexible.

### Analogy

An ordinary variable is a "room nickname" or "doorplate number." A pointer variable is a "room specifically for storing doorplate numbers"—for example:

- `int temp = 25;`: The nickname `temp` corresponds to the room with doorplate number `0x7ffeefbff5c4`, containing 25.
- `int *p = &temp;`: The pointer variable `p` is a "small room" that only stores a doorplate number—specifically, it stores the doorplate number of `temp` (`&temp` means "take the address of `temp`").
- `*p = 30;`: "Dereferencing"—using the doorplate number in `p`, directly put 30 into the corresponding room (equivalent to `temp = 30`).

### Example

```c
#include <stdio.h>

int main() {
    // Ordinary room: nickname temp, doorplate &temp, content 25
    int temp = 25;
    // Pointer room: p stores temp's doorplate number (& is "address-of")
    int *p = &temp;

    printf("temp's nickname value: %d\n", temp);     // Outputs 25
    printf("temp's doorplate number: %p\n", &temp);    // Prints address (e.g., 0x7ffeefbff5c4)
    printf("Doorplate number inside pointer p: %p\n", p);      // Exactly the same as &temp
    printf("Operating on the room via p: %d\n", *p);       // Dereference, outputs 25

    // Use pointer to directly modify room content
    *p = 30;
    printf("temp's value after modification: %d\n", temp);    // Outputs 30

    // Pointer points to another variable
    int num = 50;
    p = &num;  // Put num's doorplate number into p
    printf("Accessing num via p: %d\n", *p);        // Outputs 50
    return 0;
}
```

### Key Points to Note

- The core of pointers is "addresses": `&` is "address-of" (get the room's doorplate number), `*` is "dereference" (find the room by the doorplate number, like using the doorplate number to find the room and operate on its contents).
- Mastering "single-level pointers" is enough; no need to delve into complex uses like double pointers, pointer arrays, etc.
- Pointer variables must also have a specified type (e.g., `int *p`) to ensure the "room layout" being operated on matches.
- For `int *p = &temp`, `p` represents the room storing a doorplate number, while `*p` represents the content stored in the room whose doorplate number is stored in `p` (the value of the variable `p` points to).

#### Tip:

> You must have heard of the `scanf()` function, usually used like this:
> 
> ```c
> int n;
> scanf("%d", &n);
> ```
> 
> Right?
> 
> Actually, the `&` in `&n` here means "take the address."
> 
> Also, don't forget to write `&` and `*` when writing pointers.

## 5. Macros and typedef: Giving C Language "Aliases and Shortcut Commands"

These two are C language's "lazy tools"—making code shorter and easier to understand. They are core means of simplifying code in large programs.

### 5.1 Macro Definition (#define): Shortcut Commands / Constant Aliases

#### Analogy

Macro definition is like "giving a long sentence an abbreviation"—e.g., abbreviating "No. 88, Jianguo Road, Chaoyang District, Beijing" to "company address," or abbreviating "1000000" to "DELAY_TIME."

- Purpose 1: Define constants (avoid magic numbers, make code readable).
- Purpose 2: Define shortcut operations (abbreviate a block of code into one name).

#### Example

```c
#include <stdio.h>

// Purpose 1: Define constant aliases
#define PI 3.14159
#define MAX_SCORE 100
#define GREETING "Hello, C Language!"

// Purpose 2: Define shortcut operations (calculate circle area), not commonly used
#define CIRCLE_AREA(r) (PI * (r) * (r)) // Note: Added parentheses around r for safety

int main() {
    // Using constant macros
    printf("Pi: %.5f\n", PI);
    printf("Full score: %d\n", MAX_SCORE);
    printf("Greeting: %s\n", GREETING);

    // Using shortcut operation macro
    float radius = 5.0f;
    float area = CIRCLE_AREA(radius);
    printf("Area of circle with radius %.1f: %.2f\n", radius, area);

    // Macro-defined delay operation (simulating time consumption)
    #define DELAY() for(int i=0; i<100000; i++); // Note: No semicolon at end of macro definition usually
    DELAY();  // Execute delay (empty loop)
    printf("Delay completed\n");
    return 0;
}
```

### 5.2 typedef: Type Aliases

#### Analogy

typedef is like "giving a room layout an alias"—e.g., abbreviating "4-square-meter int large room" to "INT," or abbreviating "int* room for storing doorplate numbers" to "P_INT."

- Core: Only changes the name, not the essence of the type.
- Common scenarios: Simplifying the writing of complex types (e.g., pointers, structures).

#### Example

```c
#include <stdio.h>

// Give aliases to basic types
typedef int INT;
typedef float FLOAT;
// Give aliases to pointer types
typedef int* P_INT;
// Give aliases to unsigned types
typedef unsigned char uint8_t;
typedef unsigned int uint32_t;

int main() {
    // Define variables using aliases, identical to the original type
    INT age = 28;          // Equivalent to int age = 28;
    FLOAT weight = 65.5f;  // Equivalent to float weight = 65.5f;
    printf("Age: %d, Weight: %.1fkg\n", age, weight);

    // Define variables using pointer alias
    P_INT p = &age;        // Equivalent to int *p = &age;
    *p = 29;
    printf("Age after modification: %d\n", age);

    // Define variables using unsigned aliases
    uint8_t num1 = 255;    // 1-byte unsigned number, range 0-255
    uint32_t num2 = 4294967295U;  // 4-byte unsigned number
    printf("uint8_t value: %u\n", num1);
    printf("uint32_t value: %lu\n", num2);
    return 0;
}
```

### Key Points to Note

- Macro definition is "preprocessor substitution" (direct text replacement before compilation), typedef is "type renaming" (recognized during compilation).
- Macro definitions do not end with a semicolon, otherwise it may cause substitution errors.
- Aliases defined by typedef are "types," they cannot directly define constants. Their purpose should be distinguished from macro definitions.

## Core Summary for Getting Started

1. Variables are "memory rooms," type determines room size, variable name is the room nickname.
2. Conditionals/loops are the program's "logic control": `if` makes choices, `for`/`while` perform repetitive operations.
3. Functions "encapsulate operations," packaging repetitive code to make programs more concise and maintainable.
4. Pointers "operate on addresses," directly controlling memory through doorplate numbers, a core feature of C.
5. Macros/typedef are tools for "simplifying code": macros replace code, typedef replaces types.

Learning advice: First write small examples to thoroughly understand single知识点 (e.g., practice variables + printing first, then conditionals + loops), then combine multiple知识点 (e.g., use functions to encapsulate loop logic, use pointers to modify variables inside functions). Progress step by step to quickly master the core usage of general C programs.

## What to Learn Next?

Structures, file operations, dynamic memory allocation, etc.

More advanced languages like C++, Java, Python, etc.

You can also go learn embedded content like STM32. This document is basically sufficient for embedded use.
