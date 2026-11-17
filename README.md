# Lab 09: Exploring D&C Algorithms

**Instructions:** Work in small groups to complete the following exercises. Try sketching out your work on the whiteboards or scratch paper. Everyone should submit their own answers to the exercises, but you are encouraged to discuss your reasoning with your group members.

Name(s): ___________________________

---

## Exercise 1: Recurrence Extraction

Consider the following divide-and-conquer algorithm, which takes an array $A$ of $n$ numbers as input and returns a single number. 

```text
Procedure Mystery(A, n)
    if n <= 1:
        return A[1]                              // Base case
        
    k = floor(n / 3)                             // Find the one-third point
    
    left = Mystery(A[1..k], k)                   // Recur on the left third
    right = Mystery(A[k+1..n], n - k)            // Recur on the rest
    
    total = 0 
    for i = 1 to n:
        total = total + (A[i] * left * right)    // Combine results
        
    return total
```

### Part A: The Recurrence Relation
Let $T(n)$ be the running time of `Mystery` on an input of size $n$. Write down a recurrence relation for the worst-case running time $T(n)$. You may assume $n$ is a power of 3 for simplicity. *(Note: You do not need to solve the recurrence relation yet, just formulate it).* O(n)

### Part B: Visualizing Algorithm Behavior
Without solving the recurrence, look closely at the recursive calls and the combine step. If you were to draw the recursion tree for this algorithm, what would it look like? Is the tree balanced or skewed? 

---
left seems m/3   right seems 2n/3? so with O(n)
T(n) = T(n/3) + T(2n/3) + O(n)?  watched a tutorial on how to do this since my head hurt, my bad if it's wrong

n on top left n/3 right 2n/3 left bottom should be n/9 and 2n/9? and right bottom should be 2n/9 amd 4n/9 so its skewed due to the 4n/9?


## Exercise 2: Unrolling the Recursion Tree

Suppose you have developed a new divide-and-conquer algorithm. You analyze your pseudocode and determine that its worst-case running time $T(n)$ satisfies the following recurrence relation:

$$T(n) \leq 3T\left(\frac{n}{2}\right) + cn^2 \quad \text{for } n > 1$$
$$T(1) \leq c$$

where $c$ is a positive constant. 

### Part C: Recursion Tree Analysis

Analyze the running time of the algorithm by unrolling the recursion tree. Specifically, answer the following questions:

1. **Root Work:** Find the amount of work done at the root level (level $0$) of the recursion tree.  cn^2
2. **First Levels:** Find the amount of work done at level $1$ and level $2$ of the recursion tree. 3cn^2/4 and 9cn^2/16
3. **Tree Height:** Find the height of the recursion tree (at what level does the input size reach $1$?). log (small2) n

**Bonus!** Find a general formula for the total work done at level $i$ of the recursion tree.

---

## Exercise 3: Reflection

1. During lecture last week, we looked at two different divide-and-conquer algorithms. What were these algorithms and what problems did they solve?
Merge sort if for sorting large sets
selection sort is for sorting smaller data sets


2. How do the algorithms you analyzed in this lab compare to the ones we discussed in lecture? Specifically, each algorithm differs from the two we discussed in lecture in one important way. For each of the algorithms above, what is that difference?

Divides and combines then region near split. The ability ti look into overlap