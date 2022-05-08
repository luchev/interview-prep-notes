# Sorting

Sorting algorithms order a collection of elements.

We can sort a set of elements whose elements are in a partial order. A partial order is a relation with the following properties:

1. Antisymmetry - For every 2 elements in the set $$A, B$$, if $$A \le B$$ and $$B \le A$$ then $$A=B$$.
2. Transitivity - For every 3 elements in the set $$A, B, C$$, if $$A \le B$$ and $$B \le C$$ then $$A \le C$$.
3. Reflexivity - For every element in the set $$A$$, $$A \le A$$.

## Properties

### **Stability**

A sorting algorithm is stable if two equal objects appear in the same order in the sorted output as they appeared in the unsorted input.

#### Example

Input: $$1, 2, 3_a, 8, 5, 3_b$$. Here $$3_a$$ and $$3_b$$ are just 3s but we have marked them to follow what happens with them after the sorting.

Stable sort output: $$1,2,3_a,3_b,5,8$$

Unstable sort output: $$1,2,3_b,3_a,5,8$$ - this is a non-deterministic result (i.e. sometimes it can be $$3_a, 3_b$$, while other times $$3_b, 3_a$$)

### **Adaptivity**

Indicates whether the sorting algorithm runs faster for inputs that are partially or fully sorted. If an algorithm does not have this property it has the same time complexity for sorted and unsorted input. If an algorithm is adaptive it runs faster on sorted input than on unsorted input.

### **Locality**

An algorithm that heavily uses the processor cache to speed up its execution. The data processed needs to be sequential in memory.

### **In-place**

Uses a constant extra memory. In-place sort means the elements are swapped around. Out-of-place usually means that an extra array of the same size as the input is used and elements are moved between the two arrays.

### **Online**

Indicates if an algorithm needs all the items from the input to start sorting. If an algorithm is online it can start sorting input that is given in parts. If an algorithm is offline it can start sorting only after it has the whole input. Online algorithms can read from a stream and process data as it arrives.

### **External**

Allows sorting data that cannot fit into memory. Such algorithms are designed to sort massive amounts of data (Gigabytes, Terabytes, etc.) All algorithms can be used to sort data that cannot fit into memory, but this property indicates if the algorithm is optimized for operations with files.

### **Parallel**

An algorithm that can be run on multiple threads at the same time, speeding the running time.

### **Number of comparisons**

The number of comparisons evaluates how many times we need to compare 2 different elements. For most sorting algorithms this represents the time complexity. There are also sorting algorithms that do not rely on comparisons. The lower bound for any algorithm using comparisons is $$\mathcal{O}(n \times log(n))$$.

### **Number of swaps**

The number of swaps evaluates how many times we need to swap 2 different elements. This matters when the elements we're sorting are huge in size (tens or hundreds of MBs). While this does not affect the complexity analysis, it can affect the actual runtime of an algorithm.
