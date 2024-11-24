https://www.geeksforgeeks.org/c-implementation-double-ended-queue/
A **double-ended queue** (deque) is a data structure that allows insertion and deletion of elements from both ends—front and back. This flexibility makes it a versatile option compared to a simple queue (FIFO) or stack (LIFO). Here’s a detailed breakdown of a deque, its advantages, and its operations:

### Characteristics of a Deque

1. **Operations**:
   - **Insertions**: You can add elements to both the front and the back.
   - **Deletions**: You can remove elements from both the front and the back.
   - **Peek**: You can view the element at the front or the back without removing it.

2. **Structure**:
   - A deque can be implemented using various underlying data structures, such as:
     - **Linked Lists**: Nodes point to each other, allowing O(1) insertions and deletions from both ends.
     - **Arrays**: A circular array can be used, where indices wrap around, allowing efficient access and modification.

### Advantages of Deque Over Simple Queue

1. **Flexibility**:
   - In a simple queue, you can only add to the back and remove from the front. A deque allows you to add and remove from both ends, making it more flexible for various applications.

2. **Versatile Use Cases**:
   - Deques are suitable for algorithms that require access to both ends of the structure. For example:
     - **Task Scheduling**: You might want to prioritize tasks by adding them to the front or back based on their urgency.
     - **Sliding Window Problems**: Deques are often used to maintain a window of values efficiently, allowing easy access to both the current and past elements.

3. **Efficiency**:
   - Operations on both ends of a deque can be done in O(1) time, making it efficient for dynamic scenarios where the dataset frequently changes.

### Operations in a Deque

1. **Insertion**:
   - **Insert Front**: Adds an element to the front of the deque.
   - **Insert Back**: Adds an element to the back of the deque.

   **Pseudocode**:
   ```
   function insertFront(deque, value):
       newNode = createNode(value)
       newNode.next = deque.head
       if deque.head is not None:
           deque.head.prev = newNode
       deque.head = newNode
       if deque.tail is None:
           deque.tail = newNode  // If deque was empty, update tail

   function insertBack(deque, value):
       newNode = createNode(value)
       if deque.tail is None:
           deque.head = newNode  // If deque is empty, update head
       else:
           deque.tail.next = newNode
           newNode.prev = deque.tail
       deque.tail = newNode
   ```

2. **Deletion**:
   - **Delete Front**: Removes the element at the front of the deque.
   - **Delete Back**: Removes the element at the back of the deque.

   **Pseudocode**:
   ```
   function deleteFront(deque):
       if deque.head is None:
           return None  // Deque is empty
       deletedValue = deque.head.value
       deque.head = deque.head.next
       if deque.head is not None:
           deque.head.prev = None
       else:
           deque.tail = None  // Deque became empty
       return deletedValue

   function deleteBack(deque):
       if deque.tail is None:
           return None  // Deque is empty
       deletedValue = deque.tail.value
       deque.tail = deque.tail.prev
       if deque.tail is not None:
           deque.tail.next = None
       else:
           deque.head = None  // Deque became empty
       return deletedValue
   ```

3. **Peek**:
   - **Peek Front**: Returns the element at the front without removing it.
   - **Peek Back**: Returns the element at the back without removing it.

   **Pseudocode**:
   ```
   function peekFront(deque):
       if deque.head is None:
           return None  // Deque is empty
       return deque.head.value

   function peekBack(deque):
       if deque.tail is None:
           return None  // Deque is empty
       return deque.tail.value
   ```

### Conclusion

A double-ended queue (deque) offers significant advantages in flexibility and efficiency over simple queues. Its ability to add and remove elements from both ends makes it suitable for a variety of applications where order matters but the data structure needs to accommodate frequent changes from both ends. Whether for task scheduling, implementing sliding window algorithms, or other dynamic data needs, a deque can be an ideal choice. If you have any further questions or specific use cases in mind, feel free to ask!

---
## algos

Sure! Here are the algorithms for the operations in a double-ended queue (deque) along with explanations for each operation.

### 1. Insertion Algorithms

#### Insert Front (check copy for shot and ezz algo)

**Algorithm**:
1. Create a new node with the given value.
2. If the deque is empty, set both head and tail to the new node.
3. If the deque is not empty:
   - Set the new node's next pointer to the current head.
   - Update the current head's previous pointer to point to the new node.
   - Update the head pointer to the new node.

**Pseudocode**:
```pseudocode
function insertFront(deque, value):
    newNode = createNode(value)
    if deque.head is None:
        // Deque is empty
        deque.head = newNode
        deque.tail = newNode
    else:
        // Insert at the front
        newNode.next = deque.head
        deque.head.prev = newNode
        deque.head = newNode
```

#### Insert Back

**Algorithm**:
1. Create a new node with the given value.
2. If the deque is empty, set both head and tail to the new node.
3. If the deque is not empty:
   - Set the current tail's next pointer to the new node.
   - Update the new node's previous pointer to the current tail.
   - Update the tail pointer to the new node.

**Pseudocode**:
```pseudocode
function insertBack(deque, value):
    newNode = createNode(value)
    if deque.tail is None:
        // Deque is empty
        deque.head = newNode
        deque.tail = newNode
    else:
        // Insert at the back
        deque.tail.next = newNode
        newNode.prev = deque.tail
        deque.tail = newNode
```

### 2. Deletion Algorithms

#### Delete Front

**Algorithm**:
1. Check if the deque is empty.
   - If it is, return an indication of underflow (e.g., `None`).
2. Store the value of the current head node.
3. Update the head pointer to the next node.
4. If the new head is not `None`, update its previous pointer to `None`.
5. If the new head is `None`, set the tail to `None` (the deque is now empty).
6. Return the value of the deleted node.

**Pseudocode**:
```pseudocode
function deleteFront(deque):
    if deque.head is None:
        return None  // Deque is empty
    deletedValue = deque.head.value
    deque.head = deque.head.next
    if deque.head is not None:
        deque.head.prev = None
    else:
        deque.tail = None  // Deque became empty
    return deletedValue
```

#### Delete Back

**Algorithm**:
1. Check if the deque is empty.
   - If it is, return an indication of underflow (e.g., `None`).
2. Store the value of the current tail node.
3. Update the tail pointer to the previous node.
4. If the new tail is not `None`, update its next pointer to `None`.
5. If the new tail is `None`, set the head to `None` (the deque is now empty).
6. Return the value of the deleted node.

**Pseudocode**:
```pseudocode
function deleteBack(deque):
    if deque.tail is None:
        return None  // Deque is empty
    deletedValue = deque.tail.value
    deque.tail = deque.tail.prev
    if deque.tail is not None:
        deque.tail.next = None
    else:
        deque.head = None  // Deque became empty
    return deletedValue
```

### 3. Peek Algorithms

#### Peek Front

**Algorithm**:
1. Check if the deque is empty.
   - If it is, return `None` (or another indication of emptiness).
2. Return the value of the head node.

**Pseudocode**:
```pseudocode
function peekFront(deque):
    if deque.head is None:
        return None  // Deque is empty
    return deque.head.value
```

#### Peek Back

**Algorithm**:
1. Check if the deque is empty.
   - If it is, return `None` (or another indication of emptiness).
2. Return the value of the tail node.

**Pseudocode**:
```pseudocode
function peekBack(deque):
    if deque.tail is None:
        return None  // Deque is empty
    return deque.tail.value
```

### Conclusion

These algorithms outline how to perform the basic operations on a double-ended queue (deque). Each operation is designed to maintain O(1) time complexity, ensuring efficient insertions and deletions from both ends. If you have any specific questions or need further clarifications, feel free to ask!