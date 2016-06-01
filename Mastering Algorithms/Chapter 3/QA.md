# Chapter 3: Questions and Answers
Q: The following recursive definition has an error. What is it, and how can we fix it? For
a positive integer n, the definition, in its proper form, is common in formally computing the
running time of divide-and-conquer algorithms, such as merge sort (see Chapter 12). Merge
sort divides a set of data in half, then divides the halves in half, and continues this way
until each division contains a single element. Then, during the unwinding phase, the
divisions are merged to produce a final sorted set.

T(n) = { 1    	     	if n = 2
       { 2T(n/2) + n	if n = 1, n > 2

A: There is no terminating condition because there is no definition if n < 1, which occurs if
n = 1 with 2T(1/2) + 1. If we define T for n <= 1 this problem is solved

(Book formula)

T(n) = { 1		if n = 1
       { 2T(n/2) + n 	if n > 1

We needed to define a termination condition that is obtainable and n = 1 is obtainable, where
n = 2 was not (always)



Q: Describe a recursive approach for computing the prime factors of a number. Determine whether
the approach is tail recursive, and describe why or why not.

A: Non-tail recursive:
For number n where n >= 4, find the first factor of n and repeat for those factors until you
have a factor with no factors.

(Book answer)

F(n, P) = { P U n						if n is prime
     	  { F(n/i, P U i); i is the smallest prime factor of n	if n is not prime

Is tail recursive because continuously pass P with previous results



Q: Considering how the stack is used in executing recursive functions, what happens when
the winding phase of a recursive process never terminates, perhaps as a result of a
malformed terminating condition, as in the first question?

A: stack-overflow will eventually occur because the stack will have too many activation records
which will overflow the stack.

(Book answer) (same)



Q: Recursive functions frequently offer simple yet concise ways to describe useful computations.
Describe the computation that the following recursive definition describes:

H(n) = { 1   		      if n = 1
       { H(n - 1) + (1 / n)   if n > 1

A: This function describes a series of fractions that are 1/2 distance from each other and their
sum, as well as the number 1

(Book answer) For number n, the function calculates the harmonic series. It adds all the
fractions from 1/n to 1/1.



Q: Is the function in the previous question tail recursive? If so, describe why. If not,
describe why not and present a tail-recursive version.

A: No it is not tail recursive because the results of the previous activation record are
needed to calculate the final activation record. It can be redefined as such:

H(n, r) = { 1 + r   	      		 if n = 1
     	  { H(n - 1, r + (1 / n)	 if n > 1

(Book answer) (same)