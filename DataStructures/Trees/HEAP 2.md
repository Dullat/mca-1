Heaps are efficient data structures used to maintain a priority order among elements. They support various operations that allow quick insertion, deletion, and access to the highest or lowest priority elements, depending on whether it's a **Min Heap** or **Max Heap**.

Here’s a breakdown of the common operations on heaps:

### 1. **Insert (Insertion)**
   - **Purpose:** Add a new element to the heap.
   - **Steps:**
     1. Insert the new element at the **last position** in the heap (this maintains the complete binary tree property).
     2. **Bubble up** (or **heapify up**) the newly inserted element to restore the heap property. This means comparing it with its parent and swapping if necessary, until the heap property is satisfied.

   - **Time Complexity:** O(log n)  
     - In the worst case, you may need to bubble up through the height of the tree, which is log(n), where n is the number of elements in the heap.

   - **Example (Min Heap):**
     - Insert `3` into this Min Heap:
       ```
              1
             / \
            3   5
           / \ / \
          7  9 8 10
       ```
     - The element `3` is inserted at the last position, and then it's bubbled up to restore the heap property.

### 2. **Extract Min (or Extract Max)**
   - **Purpose:** Remove the root element (either the minimum in a **Min Heap** or the maximum in a **Max Heap**).
   - **Steps:**
     1. Swap the root element with the **last element** of the heap (the rightmost leaf).
     2. Remove the last element (which is now at the root) from the heap.
     3. **Bubble down** (or **heapify down**) the new root to restore the heap property. This means comparing the root with its children and swapping it with the smallest (in Min Heap) or largest (in Max Heap) child until the heap property is restored.

   - **Time Complexity:** O(log n)  
     - Similar to insertion, in the worst case, you may have to bubble down through the height of the tree.

   - **Example (Min Heap)**:
     - Extract the minimum (root) `1` from this Min Heap:
       ```
              1
             / \
            3   5
           / \ / \
          7  9 8 10
       ```
     - After removing `1`, we swap it with the last element `10`:
       ```
              10
             /  \
            3    5
           / \  / \
          7  9 8
       ```
     - Now, bubble down `10` to restore the heap property. Swap `10` with the smallest child, `3`, and continue bubbling down:
       ```
              3
             / \
            10  5
           / \ / \
          7  9 8
       ```

### 3. **Peek (Get Min or Max)**
   - **Purpose:** Return the root element without removing it.
   - **Steps:** Simply return the root element. This operation does not modify the heap.
   - **Time Complexity:** O(1)  
     - Since the root is always the minimum (in a **Min Heap**) or maximum (in a **Max Heap**), you can access it directly without traversing the heap.

   - **Example (Min Heap):**
     - In the heap:
       ```
              1
             / \
            3   5
           / \ / \
          7  9 8 10
       ```
     - **Peek** returns `1` without modifying the heap.

### 4. **Heapify (Build Heap)**
   - **Purpose:** Convert an unsorted array into a valid heap (either Min or Max).
   - **Steps:**
     1. Start from the **last non-leaf node** (which is at index `n//2 - 1`, where `n` is the number of elements).
     2. Apply the **heapify down** process to each node, moving towards the root. This ensures the heap property is maintained.
     3. After processing all nodes, the array will represent a valid heap.

   - **Time Complexity:** O(n)  
     - Even though each heapify operation takes O(log n), the heapify process only requires O(n) time because we perform fewer operations at lower levels of the tree. The total time complexity is linear.

   - **Example (Min Heap)**:
     - Given the array: `[5, 9, 3, 7, 8, 1, 10]`
     - After **heapify**, it will become:
       ```
              1
             / \
            3   5
           / \ / \
          7  9 8 10
       ```

### 5. **Decrease Key / Increase Key**
   - **Purpose:** Update the value of a specific element in the heap, then restore the heap property.
   - **Steps for Decrease Key** (in a Min Heap):
     1. Decrease the key of the element.
     2. **Bubble up** the element to restore the heap property.
   - **Steps for Increase Key** (in a Max Heap):
     1. Increase the key of the element.
     2. **Bubble down** the element to restore the heap property.

   - **Time Complexity:** O(log n)  
     - After changing the value, you may need to perform a bubble-up or bubble-down operation, both of which take logarithmic time.

   - **Example (Min Heap)**:
     - Consider a Min Heap:
       ```
              1
             / \
            3   5
           / \ / \
          7  9 8 10
       ```
     - Decrease the key of element `7` to `2`. The result will be:
       ```
              1
             / \
            2   5
           / \ / \
          3  9 8 10
       ```

### 6. **Delete (Delete a Specific Element)**
   - **Purpose:** Remove a specific element from the heap.
   - **Steps:**
     1. Find the element to delete.
     2. Replace it with the last element in the heap (just like in **Extract Min/Max**).
     3. Restore the heap property by either **bubbling up** or **bubbling down** the replaced element.

   - **Time Complexity:** O(log n)  
     - Finding the element might take O(n), but replacing it and restoring the heap property takes O(log n).

---

### **Summary of Heap Operations:**

| **Operation**         | **Time Complexity**   | **Description**                                    |
|-----------------------|-----------------------|----------------------------------------------------|
| **Insert**            | O(log n)              | Add an element and restore the heap property.      |
| **Extract Min/Max**   | O(log n)              | Remove the root element and restore the heap.      |
| **Peek**              | O(1)                  | Return the root element without modifying the heap.|
| **Heapify (Build Heap)** | O(n)                 | Convert an unsorted array into a valid heap.       |
| **Decrease Key / Increase Key** | O(log n)    | Update an element's value and restore the heap.    |
| **Delete**            | O(log n)              | Remove a specific element and restore the heap.    |

These operations make heaps highly efficient for managing priority queues, sorting algorithms (like **Heapsort**), and graph algorithms (like **Dijkstra's shortest path algorithm**).