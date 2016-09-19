# NP, NP complete and NP hard

# NP problems

NP problems are those for which there exists a verifier which can verify if a given solution is correct in polynomial time

All the P problems are in NP

## NP complete

A problem X is an NP complete problem if it's an NP problem and any NP problem can be reduced to X. That is there exists a polynomial time algorithm which can solve any NP problem using A. Another way of saying that is, if a NP complete problem can be solved, all the NP problems can be solved.

SAT solvers are NP complete.

## NP hard

A problem X is an NP hard problem if all the NP complete problems can be reduced to X. X doesn't have to be a NP problem

Halting problems are NP hard and can not be solved by Turing machines. The Halting problem in, given a program and an input to the program, the problem is to determine whether that problem will eventually halt when run with that input.