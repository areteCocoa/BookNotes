# Chapter 3: Recursion
Pages 27-37

- This chapter covers:
  - Basic recursion
    - A powerful principle, allows something to be defined in terms of smaller instances of self
    - Solve recursive problems with recursive functions which call themselves
  - Tail recursion
    - A type of recursion for which most compilers recognize and can optimize
    - We will make use of this because it is optimizable

## Basic Recursion
- Lets define with factorials, n!
- Iterative solution: loop through number and multiply with all numbers before it
- Recursive solution: Define n as n * (n - 1)! and n - 1 as (n - 1) * (n - 2)! until
n = 1 and we compute n!
- Two basic phases of recursive process
  - Winding: Perpetuate the recursive process, calling the same function with smaller units
    - Terminating Condition: the condition that terminates one of the subfunctions
      - Defines when it should return instead of spawning a new subcall
  - Unwinding: In which the previous instances of the function are revisited in reverse order
    - Continues until the original function call returns and then it is complete
- To fully understand C recursion, must understand more C
  - Activation: The call of a function which allocates a block of memory on the stack
  - Activation Record/Stack Frame: the block of memory from the activation
    - Consists of five regions:
      - Incoming parameters
      - Space for return value
      - Temporary storage used in evaluating expressions
      - Saved state information for when activations terminates
      - Outgoing parameters
- Stack great for storing information about function calls because of first-in-last-out
- Generating activation records and destroying them in long recursive functions can be expensive
- Use tail recursion to combat this inefficiency

## Tail Recursion
- A recursive function is 'tail recursive' if all recursive calls within it are tail recursive
- A recursive call is 'tail recursive' when it is the last statement that will be executed
within the body of a function and its return value is not a part of an expression
- Characteristic of not having an unwinding phase so compiler can optimize that
- Compiler overwrites activation records instead of stacking a new one
  - This is allowed because they are the last statement called so there is no additional computation
- Former factorial definition not tail recursive because it had to have former n data stored
in previous activation records
- Defining factorial as F(n, a), instead of F(n), where a is the sum so far allows there to be no "old" data

[END CHAPTER]