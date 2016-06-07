# Chapter 2: Pointer Manipulation
Pages 11-27

- In C, for any type T we can form a corresponding type for the variables that contain addresses in
memory where objects of T reside
- Point to object, called 'pointers'
- Very powerful and easy to misuse, create buggy unpredictable software, etc
- This chapter covers:
  - Pointer fundamentals
    - Best methods for comprehension
    - Avoiding dangling pointers
  - Storage allocation
    - Process of reserving space in memory
  - Aggregates and pointer arithmetic
    - In C, aggregates are structures and arrays
    - Arithmetic defines rules with which calcuations on pointers are performed
    - Pointers to structs important for building data structures
  - Pointers as parameters to functions
    - How C simulates call-by-reference parameter passing
    - Efficiently passing large arrays and structures
  - Pointers to pointers
    - Pointers that point to other pointers instead of pointing to data
    - Pointers to pointers are common as parameters to functions
  - Generic pointers and casts
    - Mechanisms that bypass and override C's type system
    - Generic pointers allow us to point to data without being concerned to the type
    - Casts allow us to change the type of a value temporarily
  - Function pointers
    - Pointers that point to executable code or blocks of information needed to invoke
    executable code instead of pointing to data.
    - Used to store and manage functions as it they were data

## Pointer Fundamentals
- Pointers are hard to understand conceptually but easier if you draw diagrams
  - Instead of variable names and addresses, have pointers point to actual block
  - NULL pointers with double line
- Does not point anywhere useful until we explicitly set where it points
- Dangling Pointers: pointers to invalid memory
  - Caused by:
    - Casting arbitrary integers to pointers
    - Adjusting pointers beyond bounds of array
    - Deallocating storage that one or more pointers still reference

## Storage Allocation
- Space is allocated for pointer, usually one machine word (but size can vary)
- Often vary in size, with implementation
- No space is allocated for the data is allocated when the pointer is declared
- Space for data allocated in one of two ways:
  - (1) Declaring a variable for it
  - (2) Allocating storage dynamically at runtime (malloc or realloc, for example)
- When a variable is declared, the program tells the machine how much storage to allocate
  - Automatic
  - Important when dealing with pointers to automatic variables
- Automatic Variables: Variables whose storage is allocated and deallocated automatically
when entering and leaving a block or function
- When we dynamically allocate storage in C, we get memory on the heap that we have
to keep track of and manage
   - malloc memory is valid until we call free sometime later
- Misusing dynamically allocated memory leads to memory leaks
  - Memory never freed properly by the program, even when no longer in use
- We can use consisten approaches to avoid memory leaks
- This book makes the user in charge of data structure alloc/dealloc
  - Only pointers to the data for data structures is kept, no private copies
  - Initialization usually consists of many steps
  - Destroying data usually frees all the memory

## Aggregates and Pointer Arithmetic
- One of the most common uses for pointers is referencing aggregate data
  - Arrays
  - Structs (and unions which are similar to structs but their own class as well)

### Structures
- Structure: A sequence of heterogeneous elements grouped so they can be treated as a
single datatype
- Structures allow us to group data together in meaningful bundles, pointers allow us to
link them in memory
- A linked list where the list element points to the next list element struct
- Structs may not contain a copy of themselves but may contain a pointer to a another
of the same type
   - A list element can not have a list element as a member, but may have a pointer to
   a list element as a member

### Arrays
- Array: A sequence of homogeneous elements arranged consecutively in memory
- Treated like an unmodifiable pointer
- To access a member, use array[index]
  - Because it is a pointer, it is the same as *(array + index)
    - Evaluated with the rules of pointer arithmatic
    - Add array address + index * size of the data type
- C multi-dimential arrays are stored row - column
  - array[row][column]
  - *(*(array + row) + column)

## Pointers as Parameters to Functions
- Pointers essential to calling functions in C
- Used to support type of parameter passing called 'call-by-reference'
- Using call-by-reference allows changes inside a function to a parameter to persist after
the function has left scope
- Call-by-value (the other type) only allows changes to parameters to persist within
the function

### Call-by-Reference Parameter Passing
- Formally, C only supports call-by-value parameter passing
- When parameters are passed to a function, the function gets own private copies of parameters
  - We can simulate call-by-reference by passing pointers instead of the values
- C gives us complete control over how a parameter is passed
  - This can be cumbersome
- When defining a function that takes a multidimensional array we must specify the size of
all arrays except the first
    - We must know the size of the smaller arrays in advance so we can correctly traverse
    the larger array

### Pointers to Pointers as Parameters
- In order for a function to modify a pointer (not the pointer's pointed value), you must
pass a pointer to a pointer

## Generic Pointers and Casts
- Pointers have types so that when they are dereferenced the compiler knows how to deal with them
- Sometimes we are not concerned about the type of the value
- Generic Pointers: A way around the typed pointers

### Generic Pointers
- Generic pointers allow us to point to data of any type at any time
- Declared as void *
- memcpy from the standard C library copies data from one place to another
  - Useful to be able to use it for all types of data without rewriting the function
- Allow us to build data structures that can hold any type without rewriting the structure
- void pointer is compatible with any type of pointer
  - a void pointer to a pointer is not compatible with any type of pointer, requires cast

### Casts
- To cast variable t of type T to type S, we type
  - S s = (s)t;
  - S * s = (s*)t;
    - s and t both point to the same data, but they are interpreted differently when deref'd
- Casts required when deferencing a void pointer because you can not deference a void pointer
  - The compiler needs to know some information about the type before deferencing

## Function Pointers
- Function Pointer: a pointer that points to a function/executable block of code instead of data
  - Used to treat functions as data
  - returnType (*functionName)(parameterType * parameter, parameterType * parameter2);
    - This means we can set functionName to any function that takes two parameterType pointers
    and returns returnType
- To call function pointers, just treat the variable as if it is the function
  - functionName(v1, v2)

[END CHAPTER]