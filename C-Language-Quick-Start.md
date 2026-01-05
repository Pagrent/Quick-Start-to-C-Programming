# Quick Start to C Language

## 1. Variables: Naming Memory "Rooms"

### Analogy

Computer memory is like an infinitely large "digital building," where each smallest storage unit is a "1-square-meter small room" (1 byte). Each room has a unique "house number" (memory address, like a hexadecimal number such as `0x7ffeefbff5c4`).

- **Declaring a variable**: Telling the computer, "I want to occupy this/these room(s) and give it a name."
  
- **Variable type**: The "layout" of the room – different layouts can hold different things (e.g., `char` is a 1-square-meter single room, can only hold one character; `int` is a 4-square-meter large room, can hold an integer; `float` is a room with markings, can hold a decimal number).
  
- **Assignment**: Putting something into the room.
  
- **Variable name**: A "nickname" for the room (e.g., using `temp` for temperature is much easier to remember than the house number `0x7ffeefbff5c4`).
  

### Example

```c
#include <stdio.h>  // Header file needed for general C input/output

int main() {
    // Declare variables of different types (occupying rooms of different layouts)
    char gender;       // 1-byte room, stores gender ('M' = male, 'F' = female)
    int age;           // 4-byte room, stores age (e.g., 25 years old)
    float height;      // 4-byte room with markings, stores height (e.g., 175.5cm)

    // Assignment: putting things into the rooms
    gender = 'M';
    age = 25;
    height = 175.5f;  // Note: add 'f' when assigning to a float

    // Print variables (check what's in the rooms)
    printf("Gender: %c\n", gender);
    printf("Age: %d\n", age);
    printf("Height: %.fcm\n", height);
    return 0;
}
```

### Key Points

- Variable names should be meaningful (don't use a/b/c), like `user_age`, `product_price`.
  
- When declaring a variable, you must specify its type so the computer knows how large a "room" to allocate.
  

#### Tip:

> The line
> 
> ```c
> #include <stdio.h>
> ```
> 
> means "this program needs the header file called `stdio.h`."
> 
> `stdio.h` stands for "Standard Input Output header file." This allows us to use functions like `printf` and `scanf`.
> 
> ```c
> int main() {
> 
> }
> ```
> 
> This is the main function of a C program, the "entry point" of the program. Execution starts from the main function. We'll talk more about the main function when discussing functions.
> 
> Also, you might see `//` and `/* */`. These are comments in C. Comments are for humans and don't affect program execution.  
> `//` is a single-line comment, covering everything from `//` to the end of that line.  
> `/* */` is a multi-line comment (comment block), containing everything from `/*` until the first `*/`.

## 2. Conditionals and Loops: Letting the Program "Make Choices and Repeat"

If variables are "rooms," then conditionals and loops are the "butler" – the butler decides "what to do" and "how many times to repeat something" based on rules.

### 2.1 Conditionals (if/else): The Butler Makes Choices

#### Analogy

Just like "If it's raining, bring an umbrella; otherwise, bring a hat" – the butler executes different actions based on a "condition."

- Condition: e.g., "Is the number in the room greater than 18?" (`age > 18`).
  
- Execution: If the condition is true, take the `if` branch; if false, take the `else` branch.
  

#### Example (Check if Adult)

```c
#include <stdio.h>

int main() {
    int age = 20;  // Define an age variable
    char is_adult = 0;  // 0 = minor, 1 = adult

    // Conditional: Age >= 18 means adult
    if (age >= 18) {
        is_adult = 1;
        printf("Age: %d, adult\n", age);
    } else {
        is_adult = 0;
        printf("Age: %d, minor\n", age);
    }
    return 0;
}
```

We just need to understand:

```c
if(condition) {
    things to do when condition is true;
}
else {
    things to do when condition is false;
}
```

```c
if(condition1) {
    things to do when condition1 is true;
}
else if(condition2) {
    // condition1 must be false here (because if it were true, we would have already done its tasks above)
    things to do when condition2 is true;
}
else {
    things to do when none are true;
}
```

#### 2.1.1 Logical Operators: Combining Multiple Conditions

#### Analogy

Like "must satisfy all conditions" or "satisfy at least one condition":

- **`&&` (AND)**: Both conditions must be true (similar to "and").
  
- **`||` (OR)**: At least one of the two conditions must be true (similar to "or").
  
- **`!` (NOT)**: Negation, true becomes false, false becomes true.
  

#### Example 1 (Check if Age is Between 18 and 60)

```c
#include <stdio.h>

int main() {
    int age = 25;

    // Using && to check "18 ≤ age ≤ 60"
    if (age >= 18 && age <= 60) {
        printf("Age %d is between 18 and 60\n", age);
    } else {
        printf("Age %d is not between 18 and 60\n", age);
    }

    // Using || to check "age < 18 or age > 60"
    if (age < 18 || age > 60) {
        printf("Age %d is not within typical working age range\n", age);
    } else {
        printf("Age %d is within typical working age range\n", age);
    }

    return 0;
}
```

#### Example 2 (Check if Raining)

```c
#include <stdio.h>

int main() {

    // Using ! for negation
    int is_rain = 0;  // 0 means it's not raining
    if (!is_rain) {
        printf("Not raining, can go out\n");
    } else {
        printf("Raining, bring an umbrella\n");
    }

    return 0;
}
```

#### Key Points

- `&&` has higher precedence than `||`. Use parentheses when necessary to clarify logic, e.g.:
  
  ```c
  if ((a > 0 && b < 10) || c == 5)
  ```
  
- `!` negates a single condition and is often used with boolean values or comparison expressions.
  

#### A Side Note:

> **C language is not sensitive to line breaks and indentation in code.**
> 
> That is:
> 
> ```c
> if (age >= 18) {
>     is_adult = 1;
>     printf("Age: %d, adult\n", age);
> } else {
>     is_adult = 0;
>     printf("Age: %d, minor\n", age);
> }
> ```
> 
> and
> 
> ```c
> if (age >= 18) {
> is_adult = 1;printf("Age: %d, adult\n", age);
> } else {
>     is_adult = 0;
> printf("Age: %d, minor\n", age);}
> ```
> 
> or even
> 
> ```c
> if(age>=18){is_adult=1;printf("Age: %d, adult\n",age);}else{is_adult=0;printf("Age: %d, minor\n",age);}
> ```
> 
> All three produce the same result when run.
> 
> However, for code readability, please follow conventions and don't write messily
> 
> > If a line does not end with a semicolon (e.g., inside braces), the next line should be indented by 4 spaces.
> > 
> > Operators (`+`, `-`, `*`, `/`, `&`, `%`, `!`, `=`, `<`, `>`, `<=`, `>=`, `==`) should have spaces on both sides.
> > 
> > If there is a comma or semicolon on the same line, add a space after it.

### 2.2 Loops (for/while): The Butler Repeats Tasks

#### Analogy

- **for loop**: "Do something N times explicitly" – e.g., "put numbers 1-10 into 10 rooms sequentially."
  
- **while loop**: "Do something as long as a condition is true"  
  e.g., "as long as balance > 0, deduct 10 each time until balance becomes 0."
  

#### Example 1: for Loop (Batch Assignment + Printing)

```c
#include <stdio.h>

int main() {
    // Loop 5 times, print numbers 1-5
    for (int i = 0; i < 5; i++) {  // i goes from 0 to 4, 5 times total
        printf("Current count: %d\n", i);
    }

    // Loop to assign values to an array (multiple consecutive rooms)
    int scores[5];  // 5 int rooms, storing 5 scores
    for (int j = 0; j < 5; j++) {
        scores[j] = 80 + j * 2;  // Assign 80, 82, 84, 86, 88
        printf("Score #%d: %d\n", j+1, scores[j]);
    }
    return 0;
}
```

#### Example 2: while Loop (Continuous Deduction)

```c
#include <stdio.h>

int main() {
    int balance = 35;  // Initial balance of 35 yuan

    // As long as balance > 0, deduct 10 each time
    while (balance > 0) {
        printf("Current balance: %d yuan, deducting 10 yuan\n", balance);
        balance -= 10;  // Decrease balance by 10
    }
    printf("Balance is now 0, stopping deductions\n");
    return 0;
}
```

### Key Points

- Loops must have an "exit condition," otherwise it's an "infinite loop" (e.g., `while(1)` will keep the program running forever – use with caution).
  
- The `for` loop is suitable for scenarios where the "number of iterations is known." The `while` loop is suitable for scenarios where the "number of iterations is unknown, only the termination condition is known."
  

## 3. Arrays: A Row of Consecutive "Rooms"

### Analogy

Memory is originally a series of independent rooms. An array is like telling the computer: "Give me a row of consecutive rooms of the same layout, starting from this house number, N in a row!"  
For example, `int scores[5];` means "Give me 5 consecutive int rooms (20 bytes total), and the nickname for the first room is `scores`."

- The array name (`scores`) actually represents "the house number of the first room in this row."
  
- Access using index: `scores[0]` = first room, `scores[1]` = second room ... `scores[4]` = fifth room.
  
- Indices start from 0 (a C tradition, just remember it).
  

### Example 1: Basic Declaration, Assignment, Traversal

```c
#include <stdio.h>

int main() {
    // Declare a row of 5 int rooms
    int scores[5];

    // Assign values one by one (using a loop is more elegant)
    for (int i = 0; i < 5; i++) {
        scores[i] = 80 + i * 3;  // 80, 83, 86, 89, 92
    }

    // Traverse and print
    for (int i = 0; i < 5; i++) {
        printf("Score #%d: %d\n", i+1, scores[i]);
    }
    return 0;
}
```

### Example 2: Initialization (Putting things in all at once)

```c
int nums[5] = {10, 20, 30, 40, 50};          // Full initialization
int nums2[] = {1, 2, 3};                     // Automatically infer length as 3
int nums3[5] = {0};                          // Put 0 in all rooms
```

If not initialized, the array will contain some random numbers.

### Example 3: Character Arrays and Strings

```c
char name[10] = "ZhangSan";  // Actually occupies 9 bytes, automatically adds '\0' at the end
printf("Name: %s\n", name);   // %s prints until it encounters '\0'
```

### Key Points

- Never go out of bounds with the index (`scores[5] = 100;` will modify someone else's room, possibly crashing the program).
  
- In most cases, the array name is a pointer to the first element (we'll talk about what pointers are in the pointer section).
  
- The array size must be a constant when defined (you need to specify how many rooms you want from the start).
  

## 4. Functions: Giving a "Set of Operations" a Name

C functions are essentially the same in logic as functions in high school mathematics – in math, we learn `f(x) = 2x + 1`, give the independent variable `x` a value, and get a unique result through a fixed rule; C functions encapsulate "code operations" into similar "mathematical function rules," pass "independent variables (parameters)" to them, and they execute according to preset logic and return a "function value (return value)."

- **Function definition**: Corresponds to "defining a function expression" in math (e.g., specifying the rule `f(x) = 2x + 1`). In C, it clearly states the operations to perform, the needed "independent variables" (parameters), and the returned "function value" (return value).
  
- **Function call**: Corresponds to "substituting x to calculate the value" in math (e.g., calculating `f(3)`). Calling a C function means passing values to the parameters, letting the function execute its preset operations.
  
- **Parameters**: Correspond to the "independent variables" of a math function (e.g., `x` in `f(x)`, `x` and `y` in `f(x,y)=x+y`). They are the "input values" needed for the function to execute.
  
- **Return value**: Corresponds to the "function value" in math (e.g., `7` in `f(3)=7`). It is the "result value" output after the function finishes execution.
  

A more relatable example:  
In math, defining `S(a,b) = a + b` (sum of two numbers), calculating `S(10,25)` gives 35.  
In C, defining `add(int a, int b)` (sum of two numbers), calling `add(10,25)` also gives 35 – both follow the logic of "define rule → pass values → get result."

### Example

```c
#include <stdio.h>

// Function definition: Corresponds to defining S(a,b) = a + b in math
// Parameters a, b: Correspond to the independent variables in a math function. Return value: Corresponds to the math function value (int type)
int add(int a, int b) {
    int result = a + b; // Corresponds to the calculation rule a+b in math
    return result; // Return the function value, corresponds to the result of S(a,b) in math
}

// Function definition: Function with no return value (similar to operations in math that "only execute rules, don't calculate a value")
// void means no return value, like just executing "print the values of a and b" in math, not computing a result
void print_info(char name[], int age) {
    printf("Name: %s, Age: %d\n", name, age);
}

int main() {

    // Function call: Corresponds to calculating S(10,25) in math, assign the result to sum
    int sum = add(10, 25);
    printf("Result of 10+25: %d\n", sum); // Output sum, which is S(10,25)=35

    // Function call: Pass the two "independent variables" "Zhang San" and "25", execute the printing operation
    print_info("Zhang San", 25);
    print_info("Li Si", 30);
    return 0;
}
```

### Key Points

- `main()` is the "main function" – analogous to the "main calculation entry" in math: all calculations start from the "main formula." A C program always starts execution from `main()`. Other functions (like `add`, `print_info`) must be called by `main()` (like substituting into the main formula) to run.
  
- Function parameters must match the types in the definition: Just like math `f(x)` requiring `x` to be an integer, you can't pass a string. In C, `print_info` requires a character array (name) for the first parameter, so you can't pass a number.
  
- `void` type functions have no return value: Like some operations in math that only execute (e.g., "draw a coordinate system") without producing a specific numerical result. Such functions don't need `return result;`, just `return;` (or it can be omitted).
  

## 5. Pointers: Directly Operating "Room House Numbers"

Pointers are the "core powerful move" of C. Beginners find them a bit harder to understand – but mastering pointers allows direct memory manipulation, making programs more flexible.

### Analogy

Ordinary variables are "room nicknames" or "house numbers." Pointer variables are "rooms specifically for storing house numbers" – for example:

- `int temp = 25;`: The nickname `temp` corresponds to the room at house number `0x7ffeefbff5c4`, containing 25.
  
- `int *p = &temp;`: The pointer variable `p` is a "small room" that only stores house numbers – specifically, it stores `temp`'s house number (`&temp` means "get the address of `temp`").
  
- `*p = 30;`: "Dereferencing" – using the house number stored in `p`, directly put 30 into the corresponding room (equivalent to `temp = 30`).
  

### Example

```c
#include <stdio.h>

int main() {
    // Ordinary room: nickname temp, house number &temp, content 25
    int temp = 25;
    // Pointer room: p stores temp's house number (& is "address-of operator")
    int *p = &temp;

    printf("temp's value via nickname: %d\n", temp);     // Output 25
    printf("temp's house number: %p\n", &temp);    // Print address (e.g., 0x7ffeefbff5c4)
    printf("House number stored in pointer p: %p\n", p);      // Exactly the same as &temp
    printf("Accessing room via p: %d\n", *p);       // Dereferencing, outputs 25

    // Use pointer to directly modify room content
    *p = 30;
    printf("Value of temp after modification: %d\n", temp);    // Output 30

    // Make pointer point to another variable
    int num = 50;
    p = &num;  // Store num's house number into p
    printf("Accessing num via p: %d\n", *p);        // Output 50
    return 0;
}
```

### Key Points

- The core of pointers is "address": `&` is "get address" (take the room's house number), `*` is "dereference" (find the room using the house number, like taking the house number to find the room and operate on its contents).
  
- Mastering "single-level pointers" is enough; no need to delve into double pointers, arrays of pointers, etc. for now.
  
- Pointer variables also need a specified type (e.g., `int *p`) to ensure the "room layout" being operated on matches.
  
- For `int *p = &temp`, `p` represents the room storing a house number, while `*p` represents the content stored in the room whose house number is stored in `p` (the value of the variable pointed to by `p`).
  

#### Tip:

> You must have heard of the `scanf()` function, typically used like this:
> 
> ```c
> int n;
> scanf("%d", &n);
> ```
> 
> Right?
> 
> Actually, the `&` in `&n` here means "take address."
> 
> Also, don't forget to write `&` and `*` when dealing with pointers.

## 6. Macros and typedef: Giving C Language "Aliases and Shortcuts"

These are the "lazy tools" of C – making code shorter, easier to understand, and core for simplifying code in large programs.

### 6.1 Macros (#define): Shortcut Instructions / Constant Aliases

#### Analogy

Macros are like "giving a long phrase an abbreviation" – e.g., abbreviating "88 Jianguo Road, Chaoyang District, Beijing" to "Company Address," or abbreviating "1000000" to "DELAY_TIME."

- Purpose 1: Define constants (avoid "magic numbers," making code readable).
  
- Purpose 2: Define shortcut operations (abbreviating a block of code into a name).
  

#### Example

```c
#include <stdio.h>

// Purpose 1: Define constant aliases
#define PI 3.14159
#define MAX_SCORE 100
#define GREETING "Hello, C language!"

// Purpose 2: Define shortcut operations (calculate circle area), less common
#define CIRCLE_AREA(r) (PI * r * r)

int main() {
    // Using constant macros
    printf("Pi: %.5f\n", PI);
    printf("Perfect score: %d\n", MAX_SCORE);
    printf("Greeting: %s\n", GREETING);

    // Using shortcut operation macro
    float r = 5.0f;
    float area = CIRCLE_AREA(r);
    printf("Area of circle with radius %.1f: %.2f\n", r, area);

    // Macro-defined delay operation (simulate time-consuming task)
    #define DELAY() for(int i=0; i<100000; i++);
    DELAY();  // Execute delay (empty loop)
    printf("Delay completed\n");
    return 0;
}
```

### 6.2 typedef: Type Aliases

#### Analogy

`typedef` is like "giving a room layout an alias" – e.g., abbreviating "the 4-square-meter int large room" to "INT," abbreviating "the int* room for storing house numbers" to "P_INT."

- Core: Only changes the name, not the essence of the type.
  
- Common use: Simplifying the writing of complex types (e.g., pointers, structures).
  

#### Example

```c
#include <stdio.h>

// Give aliases to basic types
typedef int INT;
typedef float FLOAT;
// Give alias to pointer type
typedef int* P_INT;
// Give aliases to unsigned types
typedef unsigned char uint8_t;
typedef unsigned int uint32_t;

int main() {
    // Define variables using aliases, identical to original types
    INT age = 28;          // Equivalent to int age = 28;
    FLOAT weight = 65.5f;  // Equivalent to float weight = 65.5f;
    printf("Age: %d, Weight: %.1fkg\n", age, weight);

    // Define variable using pointer alias
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

### Key Points

- Macros are "preprocessor text substitution" (directly replaced before compilation), `typedef` is "type renaming" (recognized during compilation).
  
- Macros don't end with a semicolon, otherwise it can cause substitution errors.
  
- Aliases defined by `typedef` are "types," cannot directly define constants. Distinguish their use from macros.
  

## Quick Start Core Summary

1. Variables are "memory rooms," types determine room size, variable names are room nicknames.
  
2. Conditionals/loops are the program's "logic control": `if` makes choices, `for`/`while` perform repetitive operations.
  
3. Functions "encapsulate operations," package repetitive code, making the program more concise and maintainable.
  
4. Pointers "operate on addresses," directly manipulate memory through house numbers, a core feature of C.
  
5. Macros/`typedef` are "code simplification" tools: macros replace text, `typedef` replaces type names.
  

Learning suggestion: First write small examples to master single concepts (e.g., practice variables + printing, then conditionals + loops), then combine multiple concepts (e.g., use functions to encapsulate loop logic, use pointers to modify variables inside functions). Progress step-by-step to quickly grasp the core usage of general C programming.

## What's Next?

Structures, file operations, dynamic memory allocation, etc.

More advanced languages like C++, Java, Python, etc.

You can also learn embedded content like STM32. This document is basically sufficient for embedded use.
