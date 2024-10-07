Here's an improved version of the notes, with clearer explanations and sample code added for the algorithms.

---

### **Study Notes on Algorithmic Strategies (with Sample Code)**

---

**Learning Objective 1: Understand when and how to apply the three algorithmic strategies of Decrease and Conquer, Divide and Conquer, and Transform and Conquer.**

---

### **1. Decrease and Conquer**

- **When to apply**: 
  - When the solution to a smaller instance of the problem helps solve the larger one.
  
- **How it works**: 
  - The problem size is reduced by a constant or a factor. The solution to the smaller instance is then extended to solve the original problem.

#### **Example 1: Insertion Sort (Decrease by a Constant)**
- **Description**: 
  - Start with the first \(n-1\) elements of the array being sorted, then insert the \(n\)-th element in the correct position.
  
- **Time Complexity**: Best case: Θ(n), Worst case: Θ(n²)

- **Sample Code (Python)**:

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        # Move elements of arr[0..i-1], that are greater than key, to one position ahead
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

# Example usage
arr = [12, 11, 13, 5, 6]
insertion_sort(arr)
print(arr)
```
- **Explanation**: For each element, find its correct position in the sorted portion of the array (from the beginning up to \(i\)).

#### **Example 2: Fake Coin Problem (Decrease by a Constant Factor)**
- **Description**: 
  - Given \(n\) coins, one is lighter. We divide the coins into two groups and compare their weights to determine which group has the fake coin.

- **Time Complexity**: Θ(log n)

- **Sample Code (Python)**:

```python
def find_fake_coin(coins):
    if len(coins) == 1:
        return coins[0]  # Base case: only one coin left

    mid = len(coins) // 2
    group1 = coins[:mid]
    group2 = coins[mid:]
    
    if sum(group1) < sum(group2):  # Fake coin is in the lighter group
        return find_fake_coin(group1)
    else:
        return find_fake_coin(group2)

# Example usage
coins = [10, 10, 10, 9]  # The coin with weight 9 is the fake one
print(find_fake_coin(coins))
```
- **Explanation**: The algorithm divides the coins into two groups and recursively checks the lighter group.

---

### **2. Divide and Conquer**

- **When to apply**: 
  - Use when the problem can be split into independent subproblems that can be solved separately and then combined.

- **How it works**: 
  - The problem is divided into smaller instances, each solved recursively, and the solutions are combined to form the overall solution.

#### **Example 1: Merge Sort (Divide and Conquer)**
- **Description**: 
  - Split the array into two halves, sort them recursively, and merge the sorted halves.

- **Time Complexity**: Θ(n log n)

- **Sample Code (Python)**:

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2  # Find the middle of the array
        left_half = arr[:mid]
        right_half = arr[mid:]

        # Recursively sort both halves
        merge_sort(left_half)
        merge_sort(right_half)

        # Merging the two halves
        i = j = k = 0
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        # Copy the remaining elements
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

# Example usage
arr = [12, 11, 13, 5, 6, 7]
merge_sort(arr)
print(arr)
```
- **Explanation**: The array is recursively split into halves, and the sorted halves are merged together.

#### **Example 2: Quicksort (Divide and Conquer)**
- **Description**: 
  - Select a pivot, partition the array around the pivot, and recursively sort the subarrays.

- **Time Complexity**: Best and Average case: Θ(n log n), Worst case: Θ(n²)

- **Sample Code (Python)**:

```python
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[0]  # Select the pivot (could also be randomized)
        left = [x for x in arr[1:] if x <= pivot]
        right = [x for x in arr[1:] if x > pivot]
        return quicksort(left) + [pivot] + quicksort(right)

# Example usage
arr = [10, 7, 8, 9, 1, 5]
print(quicksort(arr))
```
- **Explanation**: The array is partitioned based on a pivot element, and the left and right partitions are recursively sorted.

---

### **3. Transform and Conquer**

- **When to apply**: 
  - When transforming the problem into a simpler or more efficient form is beneficial.

- **How it works**: 
  - Transform the problem or data into a structure that makes it easier to solve.

#### **Example 1: GCD Algorithm (Euclidean Algorithm)**
- **Description**: 
  - This algorithm finds the greatest common divisor of two numbers by repeatedly applying the modulus operation.

- **Time Complexity**: Θ(log(min(a, b)))

- **Sample Code (Python)**:

```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

# Example usage
print(gcd(60, 24))  # Output: 12
```
- **Explanation**: The algorithm repeatedly calculates \(a \mod b\) until \(b = 0\), at which point \(a\) is the GCD.

#### **Example 2: Heapsort (Transform and Conquer)**
- **Description**: 
  - Transform the array into a max-heap, then repeatedly extract the maximum element.

- **Time Complexity**: Θ(n log n)

- **Sample Code (Python)**:

```python
def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2

    if left < n and arr[largest] < arr[left]:
        largest = left

    if right < n and arr[largest] < arr[right]:
        largest = right

    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def heapsort(arr):
    n = len(arr)

    # Build a maxheap
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # Extract elements one by one
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]  # Swap
        heapify(arr, i, 0)

# Example usage
arr = [12, 11, 13, 5, 6, 7]
heapsort(arr)
print(arr)
```
- **Explanation**: The array is transformed into a max-heap structure, and then the elements are extracted in sorted order.

---

### **Summary and Key Differences**

1. **Decrease and Conquer**:
   - Gradually reduces the problem size and builds the solution step by step.
   - Example: Insertion Sort, Fake Coin Problem.
  
2. **Divide and Conquer**:
   - Divides the problem into independent subproblems, solves them, and combines the results.
   - Example: Merge Sort, Quicksort.

3. **Transform and Conquer**:
   - Transforms the data into a more manageable form and solves it efficiently.
   - Example: Heapsort, GCD Algorithm.

---

### **Example Study Questions**

1. **What is the time complexity of Merge Sort, and why?**
   - **Answer**: The time complexity is Θ(n log n) because the array is divided into two halves recursively (log n), and merging the halves takes linear time (n).

2. **How does the Euclidean Algorithm for GCD work?**
   - **Answer**: It repeatedly calculates the remainder of the division of two numbers until the remainder is zero. The last non-zero remainder is the GCD.

3. **What is the worst-case time complexity of Quicksort, and when does it occur?**
   - **Answer**: The worst-case

 time complexity is Θ(n²), and it occurs when the pivot is always the smallest or largest element, leading to unbalanced partitions.

These notes and sample codes will make understanding these strategies easier and help you practice for your exam!
