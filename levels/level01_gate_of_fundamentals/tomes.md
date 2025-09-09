You should have a good knowledge (at least the basics) of a programming language like C or C++.
For the moment, this section gives you an overview of the essential C concepts you’ll need in reverse engineering.
## C Programming Basics
### Libraries
We include libraries at the top of a program with `#include <lib.h>`.

* **`<stdio.h>`** → input/output (`printf`, `scanf`, `fgets`, `puts`)
* **`<stdlib.h>`** → memory allocation, conversions, random numbers
* **`<stdbool.h>`** → boolean type (`true`, `false`)
* **`<time.h>`** → time functions (`time`, `clock`)

#### Insight

* Library calls often appear in disassembly as **external functions**.
* Recognizing functions like `printf`, `malloc`, or `strcpy` is  helpfull in reverse engineers by understanding code's logic.

---

###  Declaring Variables

 we must declare the variable before using it. each variable need a block of memory to save its value, the type of the variable do the job of specifying the size of this space of memory
 int -> 4 bytes ( 4*8 bits )
 char -> 1 byte
 

```c
int age = 20;      // 4 bytes
char grade = 'A';  // 1 byte
float pi = 3.14;   // 4 bytes
```

#### Insight

* Variables live in **stack frames**.
  ```
   Basic Variable Storage in memory
  ```
```
Stack → Local variables (function scope).

Heap → Dynamically allocated (malloc, calloc, free).

Data Segment → Global variables.

Text Segment → Compiled machine code (instructions).
```
---

###  The `main` Function

```c
int main() {
    return 0;
}
```
or
```c
int main(int argc, char* argv[]) {
    return 0;
}
```

#### Insight

* `argv` is an array of strings passed to the program.
* `argc` is arguments counter.

---

### Operators & Control Structures

* **Arithmetic:** `+ - * / %`
* **Comparison:** `== != < > <= >=`
* **Logical:** `&& || !`
* **Biwise:** `& | ~`

```c
if (x > 0) {
    printf("Positive\n");
} else {
    printf("Not positive\n");
}
```

#### RE Insight

* `if`/`else` compiles into `cmp` + `jz/jnz/jg/jl`.
* `for`/`while` become conditional jumps.
* `switch` often becomes a **jump table** (easy to spot in disassembly).

---

### Functions

```c
int addition(int a, int b) {
    return a + b;
}
```

#### Insight

* Functions generate **stack frames**.
* Entry: epilogue 

  ```
  push ebp
  mov ebp, esp
  sub esp, XX
  ```
* Exit: prologue 

  ```
  mov esp, ebp
  pop ebp
  ret
  ```

---

### Arrays & Matrices

```c
int arr[5] = {1, 2, 3, 4, 5};
int matrix[2][3] = { {1,2,3}, {4,5,6} };
```

#### Insight

* Arrays are **contiguous memory**.
* Indexing `arr[i]` = `*(arr + i)`.
* In assembly: `mov eax, [ebx+ecx*4]`.
* Array overflows are classic **buffer overflow exploits**.

---

### Strings

```c
char name[20] = "Alice";
printf("%s", name);
```

#### Insight

* Strings = `char[]` ending in `\0`.
* Unsafe functions (`gets`, `strcpy`) → buffer overflows.
* In RE, spotting string functions is key for vulnerability research.

---

### Pointers

```c
int x = 10;
int *p = &x;
printf("Value=%d, Address=%p", *p, p);
```

#### Insight

* Pointers = **direct memory manipulation**.
* `*p` = dereference, `&x` = address-of.
* In disassembly:

  * `mov eax, [ebx]` = load value from pointer.
  * `lea eax, [ebx+4]` = compute address.

---

### Stack

* Stack = where **local variables and return addresses** live.

Example stack operations in C (manual implementation):

```c
#define SIZE 100
int stack[SIZE], top = -1;

void push(int val) { if (top < SIZE-1) stack[++top] = val; }
int pop() { return (top >= 0) ? stack[top--] : -1; }
```

#### Insight

* Stack frames reveal function variables and calls.
* Overwriting stack variables → **stack overflow exploit**.

---

### Queue & Heap

```c
#define SIZE 100
int queue[SIZE], front=0, rear=-1;

void enqueue(int val) { if (rear < SIZE-1) queue[++rear] = val; }
int dequeue() { return (front <= rear) ? queue[front++] : -1; }
```

#### Insight

* Heap allocations (`malloc`, `free`) show up in RE as calls to `malloc@plt`.
* Heap corruption → double free, use-after-free bugs.

---


---

## Exercises

* **Exo 01:** Write a program adding two integers (user input).
* **Exo 02:** Extend to floating-point numbers.
* **Exo 03:** Print addresses of array elements → compare with disassembly.
* **Exo 04:** Swap two integers with pointers.
* **Exo 05:** Implement a `strcpy` manually → inspect assembly.
* **Exo 06:** Write recursive factorial → observe stack growth.
* **Exo 07:** Implement stack push/pop.
* **Exo 08:** Implement queue enqueue/dequeue.
* **Exo 09:** Use `malloc`/`free` and print heap addresses.

---

With this guide, you’ll learn C **and** understand how it translates to memory and assembly — a solid foundation for reverse engineering.
