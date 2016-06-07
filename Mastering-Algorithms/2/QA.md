# Question and Answers
Q: One of the difficulties with pointers is that often when we misuse them, our errors are
not caught by the compiler at compile time; they occur at runtime. Which of the following
result in compile-time errors? Which of the following result in runtime errors? Why?

a. char *sptr = "abc", *tptr;
   *tptr = sptr
Compile time error; the assignment of *tptr is to the wrong type (it does not need to be pointed
to)

b. char *sptr = "abc",*tptr;
   tptr = sptr;
No error occurs; both are strings (char *)

c. char *sptr = "abc",*tptr
*tptr = *sptr
Runtime error will likely occur because no memory for *tptr has been allocated and *tptr
(we don't know where it points)

d. int *iptr = (int *)10;
   *iptr = 11;
Likely a runtime error because assigning an int point to a fixed address is dangerous

e. int *iptr = 10;
   *iptr = 11;
Runtime error; 10 is set as the address, not the value

f. int *iptr = (int *)10;
   iptr = NULL;
No error; although it is dangerously set to 10, it is validly set to NULL immediately after



Q: Recall the calculations with pointers are performed using pointer arithmatic. If p contains
the address 0x10000000, what address does the following expression access? How many bytes are
accessed at this address?

*(p + 5)

Because the question does not state what the size of the type being stored is, there is no way
to calculate the answer.



Q: The operation list_rem_next removes an element from a linked list. If iptr is an integer
pointer we would like set to an integer removed from a list, how might we call list_rem_next
as an alternative to the approach presented in the chapter? A prototype for the function is
shown here, where list is the list, element references the element preceding the one to remove
and upon return, data references the data removed.

int list_rem_next(List *list, ListElmt *element, void **data);

list_rem_next(list, element, (void *)&iptr);
Here we cast the pointer to a single void pointer (instead of a double) because void pointers
are compatible with all pointers