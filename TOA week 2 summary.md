

---

### 1. **Decrease and Conquer**
- **Concept**: Reduce the problem size by a constant amount (typically by 1) and solve the smaller instance, then extend the solution to the original problem.
- **When to Use**: When you can solve a subproblem of reduced size and iteratively or recursively build the solution for larger instances.

#### **Key Algorithms**:
1. **Insertion Sort**:
   - **Description**: Sorts a list by repeatedly inserting each element into the correct position in the already sorted part of the list.
   - **How it works**:
     - Assume the list up to index \( i-1 \) is sorted.
     - Insert the element at index \( i \) into its correct position in the sorted portion.
   - **Time Complexity**: Worst case \( O(n^2) \); best case \( O(n) \) for nearly sorted data.

2. **Binary Search**:
   - **Description**: Efficiently searches for an element in a sorted array by repeatedly halving the search space.
   - **How it works**:
     - Check the middle element.
     - If it matches the target, return the index.
     - Otherwise, eliminate half the search space and repeat.
   - **Time Complexity**: \( O(\log n) \).

3. **Topological Sort**:
   - **Description**: Orders vertices of a Directed Acyclic Graph (DAG) such that for every directed edge \( u \to v \), vertex \( u \) appears before \( v \).
   - **How it works**:
     - Remove vertices with no incoming edges and append them to the result.
     - Continue until all vertices are processed.
   - **Time Complexity**: \( O(V + E) \), where \( V \) is the number of vertices and \( E \) is the number of edges.

4. **Generating Permutations**:
   - **Description**: Generates all permutations of a set by recursively finding permutations of subsets and inserting elements in all positions.
   - **How it works**:
     - For a list of size \( n \), generate permutations of size \( n-1 \), then insert the nth element in every possible position.
   - **Time Complexity**: \( O(n!) \).

---

### 2. **Divide and Conquer**
- **Concept**: Divide the problem into two or more smaller subproblems, solve them recursively, and combine their solutions to solve the original problem.
- **When to Use**: Suitable when a problem can be broken down into smaller, independent subproblems, and the combination of their solutions yields the solution to the full problem.

#### **Key Algorithms**:
1. **Mergesort**:
   - **Description**: A sorting algorithm that divides the array into two halves, recursively sorts them, and merges the sorted halves.
   - **How it works**:
     - Split the array into two halves.
     - Recursively sort both halves.
     - Merge the two sorted halves.
   - **Time Complexity**: \( O(n \log n) \).

2. **Quicksort**:
   - **Description**: A sorting algorithm that selects a pivot, partitions the array into elements smaller and greater than the pivot, and recursively sorts both partitions.
   - **How it works**:
     - Select a pivot element.
     - Partition the array such that all elements less than the pivot are to its left, and all elements greater are to its right.
     - Recursively sort the partitions.
   - **Time Complexity**: \( O(n \log n) \) on average; worst case \( O(n^2) \).

3. **Strassen’s Algorithm (Matrix Multiplication)**:
   - **Description**: A divide and conquer algorithm that reduces the number of multiplications required for matrix multiplication.
   - **How it works**:
     - Split matrices into submatrices.
     - Multiply and add the submatrices recursively.
     - Combine the results to form the final matrix.
   - **Time Complexity**: \( O(n^{2.81}) \), compared to the standard \( O(n^3) \).

4. **Closest Pair of Points (Geometric Problem)**:
   - **Description**: Finds the pair of points in a plane that are closest to each other.
   - **How it works**:
     - Sort the points by their x-coordinates.
     - Recursively divide the points into left and right halves.
     - Find the closest pair in both halves and combine.
   - **Time Complexity**: \( O(n \log n) \).

5. **Karatsuba Algorithm (Fast Integer Multiplication)**:
   - **Description**: A divide and conquer algorithm that reduces the number of multiplications in large integer multiplication.
   - **How it works**:
     - Split each number into two halves.
     - Recursively multiply the halves and combine using fewer operations.
   - **Time Complexity**: \( O(n^{\log_2 3}) \), or approximately \( O(n^{1.585}) \).

---

### 3. **Transform and Conquer**
- **Concept**: Transform the problem or its representation into a simpler or more convenient form, then solve it. The transformation can involve instance simplification, representation change, or problem reduction.
- **When to Use**: Useful when transforming a problem can simplify its structure or reduce its complexity, or when reducing it to a different, easier-to-solve problem.

#### **Key Algorithms**:
1. **Presorting**:
   - **Description**: Many problems can be solved more efficiently once the input is presorted.
   - **How it works**:
     - Sort the input list.
     - Solve the problem on the sorted list.
     - Examples: Finding duplicates, closest pair of points, convex hull.
   - **Time Complexity**: \( O(n \log n) \) for sorting.

2. **Gaussian Elimination**:
   - **Description**: A method to solve systems of linear equations by transforming the system into an upper triangular form and using back substitution.
   - **How it works**:
     - Use row operations to eliminate variables.
     - Once in triangular form, solve the system by back substitution.
   - **Time Complexity**: \( O(n^3) \).

3. **Horner’s Rule**:
   - **Description**: Optimizes polynomial evaluation by restructuring it to minimize the number of multiplications.
   - **How it works**:
     - Rewrite the polynomial in a nested form.
     - Evaluate the polynomial using a loop that performs \( O(n) \) multiplications.
   - **Time Complexity**: \( O(n) \).

4. **Binary Exponentiation**:
   - **Description**: Efficiently computes powers of a number using the binary representation of the exponent.
   - **How it works**:
     - Express the exponent in binary.
     - Multiply the base accordingly by squaring and multiplying only when the binary digit is 1.
   - **Time Complexity**: \( O(\log n) \).

5. **LCM Reduction Using GCD**:
   - **Description**: Computes the least common multiple (LCM) of two numbers by reducing the problem to finding the greatest common divisor (GCD).
   - **How it works**:
     - Use the relation: \( \text{LCM}(a, b) = \frac{a \times b}{\text{GCD}(a, b)} \).
     - Compute the GCD using Euclid’s algorithm.
   - **Time Complexity**: \( O(\log \min(a, b)) \).

---

### Differences Between the Strategies:

- **Decrease and Conquer**: Reduces the problem size incrementally and builds the solution step by step (usually by removing one element at a time). It's often iterative or recursive and involves constant reductions.
- **Divide and Conquer**: Splits the problem into independent subproblems, solves them, and then combines their solutions. It’s recursive and handles problems in parallel subproblems.
- **Transform and Conquer**: Modifies the problem’s structure or reduces it to another problem for easier solving. It focuses on transformation before solving.

