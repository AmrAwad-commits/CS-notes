# CS Fundamentals & Algorithms — Notes

A personal knowledge base covering procedural programming, data structures, algorithms, complexity analysis, sorting, and STL.

## 📁 Contents
1. [Programming Fundamentals](#1-programming-fundamentals)
2. [Arrays, Structs & Pointers](#2-arrays-structs--pointers)
3. [Number Theory Basics](#3-number-theory-basics)
4. [Strings & Quick Tricks](#4-strings--quick-tricks)
5. [Algorithms & Complexity](#5-algorithms--complexity)
6. [Sorting Algorithms](#6-sorting-algorithms)
7. [STL & Data Structures](#7-stl--data-structures)
8. [Hashing](#8-hashing)

---

## 1. Programming Fundamentals

### Execution Flow
**Sequential execution**: Normally, statements in a program are executed one after another, in the order they're written.

**Transfer of control**: Control statements let you specify that the next statement executed may be different from the next one in sequence.

- **Selection control statements**: `if`, `switch`
- **Repetition control statements**: `while`, `do-while`, `for`

### Expressions
- **Relational expression**: `>`, `>=`, `==`, `!=`, `<`, `<=`
- **Arithmetic expression**: evaluates to `0` (false) or non-zero (true)

### Procedural Programming
A programming paradigm that structures a program by breaking it down into a series of steps or procedures — a collection of functions to solve the main problem.

### Functions
- **Built-in function**: ready-made
- **User-defined function**: tailored by the programmer
  - **Prototype** — declared before `main`
  - **Function definition** — placed after `main`
  - **Invoking function** — called inside `main`

**Parameters:**
- Call by value
- Call by reference

### Variable Scope & Lifetime
| Type | Description |
|------|-------------|
| Local variable | Declared within a function (or block) |
| Global variable | Declared outside every function/definition |
| Automatic variable | Created when the block/function starts, destroyed when it ends |
| Static variable | Initialized once, lives until the program ends (keeps its value) |

### Error Types
Syntax error · Runtime error · Linker error · Logical error · Semantic error

---

## 2. Arrays, Structs & Pointers

### Array (Homogeneous)
A collection of a fixed number of elements, all having the same data type.
- Arrays are **passed by reference only**.
- To prevent a function from modifying an array, add `const` before it:
  ```cpp
  void calc(const int arr[], int size);
  ```

### Struct (Heterogeneous)
A collection of a fixed number of components (members) accessed by name; members can have different data types.

**Array** vs **Struct**:
- Array: fixed number of elements, all the *same* type, accessed by index/address.
- Struct: fixed number of members, can be *different* types, accessed by name.

### Pointer
A variable whose value is the address of another variable.
```cpp
int *ptr = &x;
```

### Sub Array
A contiguous block of the original array's elements.
- Number of possible sub-arrays: `n*(n+1)/2`

### Sub Sequence
A sequence formed by deleting some (or no) elements without changing the order of the remaining elements.
- Number of possible sub-sequences: `n²` (more precisely `2ⁿ`, including the empty subsequence)

---

## 3. Number Theory Basics

- **Factorial**: the product of all positive integers less than or equal to the number.
- **Prime Numbers**: a number greater than 1 whose only factors are 1 and itself.
- **Palindrome Number**: a number that reads the same forward and backward.
- **GCD**: Greatest Common Divisor.
- **Fibonacci**: `Fib(n) = Fib(n-1) + Fib(n-2)`, where `Fib(1) = 0`, `Fib(2) = 1`.

---

## 4. Strings & Quick Tricks

### Building a String — Complexity Matters
```cpp
h = s[i] + h;   // O(n)  — creates a new string each time
h += s[i];      // O(1)  — amortized, appends in place
```

### Over-statement vs Under-statement (problem-solving mindset)
- **Over-statement** → long solution
- **Under-statement** → quick solution

### Handy C++ String Functions
```cpp
getline(cin, s, '\\');   // reads chars from cin until it finds '\'
stoi(s);                 // converts string to integer, limited to ~2*10^9
```
- `o mod N == 0` — divisibility check
- `s.substr(x, numOfChars)` — extract a substring starting at index `x` with a given length

---

## 5. Algorithms & Complexity

### Major Factors for an Application
Performance (time & space) · Usability · Security · Maintainability · Reliability

### Algorithm
A sequence of steps that transforms some input into an output to solve a problem.

**Testing an Algorithm:**
1. Prove its correctness
2. Measure time efficiency
3. Measure space (memory) efficiency

**Where Algorithms Show Up:** Compilers, network routing, operating systems, graphics, cryptography, databases, search engines, computer vision, machine learning.

### Data Structure
A data organization, management, and storage format that enables efficient access and modification.

### Function
A self-contained block of statements that performs a specific task.

### Dynamic Programming (DP)
Reduces the time complexity of a recursive function (by avoiding redundant recomputation).

### Recursive Function
A function that calls itself with a smaller input until it reaches a base case.

### Big O Notation
The largest term in the equation is the one that dominates.

### Average Case
The expected order of an algorithm; involves probability and considers different cases.

### `#define`
A preprocessing instruction.

### Problem Types
- **Decision Problem** — True or False
- **Optimization Problem** — calculate minimization or maximization
- **Counting Problem** — count something

### Monotonic Function
A function that is either non-increasing or non-decreasing.

### Intuition in Algorithms & Problem Solving
- Seeing the core idea behind a solution
- Understanding *why* an approach works
- Predicting behavior without formal proof
- Recognizing patterns from similar problems

---

## 6. Sorting Algorithms

### Complexity Classes
| Category | Algorithms | Complexity |
|----------|-----------|------------|
| Simple / inefficient | Bubble sort, Selection sort, Insertion sort | O(n²) |
| Efficient | Merge sort, Quick sort, Heap sort | O(n·log n) |

### Insertion Sort
Based on "incremental thinking" — take an element and insert it into its correct location. Performs fewer swaps than Bubble sort.

### Selection Sort
The algorithm's number of operations doesn't depend on the input data — this makes its **best, average, and worst case complexity the same**.

### Heap Sort
Works like Selection sort conceptually: it locates the largest (or smallest) value and places it in the final array, then repeats for the next largest, and so on.
- Selection sort takes O(n) to *locate* the smallest element.
- Heap sort locates the minimum in O(1) but takes O(log n) to *remove* it.
- Overall Big O for Heap sort: **O(n log n)**.

### Count Sort
Non-comparison-based sorting; works by counting the occurrences of each distinct element (using frequency of elements).
- Best case and worst case: **Θ(n + k)** time and space
- Very fast
- **Disadvantage**: only works for integers (not strings), and integers must be sorted within a limited range

### Language Internals
- **C++ `std::sort`** uses **Introsort** — a hybrid of Quick sort, Heap sort, and Insertion sort.
- **Python `sort`** uses **Timsort** — a hybrid of Merge sort and Insertion sort.

---

## 7. STL & Data Structures

### Iterator
A pointer-like object used to traverse and access elements within STL containers.

### STL Containers
| Category | Containers |
|----------|-----------|
| Pair | `pair` |
| Sequence | `vector`, `array`, `deque`, `list`, `forward_list` |
| Container adapters | `stack`, `queue`, `priority_queue` |
| Associative | `set`, `unordered_set`, `map`, `unordered_map` |

---

## 8. Hashing

**Hashing** is the process of converting data of any size into a fixed-length string of characters — called a hash — using a mathematical function (hash function).

### Real-World Uses
- **Search engines**: used by Google and Yahoo
- **DBMS**: indexing mechanisms used to speed up access
- **Program compilation**: error checking
