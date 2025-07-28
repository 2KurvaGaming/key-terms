# 📌 What is a Function Prototype?

## In C, a function prototype is like a "preview" or "announcement" of a function. It tells the compiler:

The name of the function,
What type of value it returns (like a number, text, etc.),
What type of inputs (arguments) it expects.
But — and this is important — a prototype does not include the actual code (the "body") of the function. It just gives the structure.

🔤 Basic Syntax
A function prototype looks like this:

return_type function_name(type1 parameter1, type2 parameter2, ...);
For example:

int add(int a, int b);
Let’s break this down:

int → the function will return an integer.
add → the name of the function.
(int a, int b) → it takes two inputs, both integers, named a and b.
The semicolon ; → this ends the line, because it’s just a declaration, not the full function.
🧠 Why Do We Need Prototypes?
In C, the compiler reads your code from top to bottom. So if you try to use a function before the compiler has seen it, it gets confused.

Here’s an example of a problem:

#include <stdio.h>

int main() {
    int result = add(5, 3);  // ERROR: Compiler doesn't know 'add' yet!
    printf("Result: %d\n", result);
    return 0;
}

int add(int a, int b) {
    return a + b;
}

This might cause a warning or error because main() calls add() before add() is defined.

✅ Solution: Use a prototype at the top!

#include <stdio.h>

// Function prototype - tells the compiler: "add() exists!"
int add(int a, int b);

int main() {
    int result = add(5, 3);  // Now it's OK!
    printf("Result: %d\n", result);
    return 0;
}

// Full function definition (body)
int add(int a, int b) {
    return a + b;
}

Now the compiler knows about add() before it’s used.

🎯 Key Points (Summary)
Concept	Explanation
Purpose	Helps the compiler check if you're using a function correctly (right number and types of arguments).
Placement	Usually written at the top of the file, after #include lines.
Semicolon	Prototypes end with ; — they don’t have { } or code inside.
Not Required	If you define the full function before you use it, you don’t need a prototype. But it’s good practice to use one.
Header Files	In bigger programs, prototypes are often placed in .h files so multiple .c files can use them.
✅ Example with No Return Value
Some functions don’t return anything. We use void:

void greet(char name[]);  // Prototype: function called 'greet' that takes a string

🧩 Think of It Like a Contract
A function prototype is like saying:

"Hey compiler, I promise there will be a function called add that takes two integers and returns an integer. Don’t panic when you see it used — it’s coming!"

💡 Final Tip
Even as a beginner, getting used to writing prototypes (or placing functions above main()) will help you avoid confusion and errors as your programs grow.
