### What is a **Collision**?

https://www.javatpoint.com/hash-table

A **collision** occurs in hashing when two different pieces of data (keys) are mapped to the **same hash value** by the hash function. Since the hash function is supposed to map each key to a unique index or slot in the hash table, when two keys have the same hash value, it causes a "collision."

Imagine the hash table as a row of boxes, and each key is assigned to a box based on its hash value. However, sometimes two different keys end up pointing to the same box (or index). This is a **collision**.

### Example of a Collision:

Let's say we have a hash table with 5 slots (indexes 0 to 4), and we're using a simple hash function that gives the remainder when dividing by 5.

- For key "apple":  
  Hash value = sum of ASCII values of characters in "apple" % 5 = 532 % 5 = 2.
  So, "apple" is placed in slot 2.

- For key "mango":  
  Hash value = sum of ASCII values of characters in "mango" % 5 = 532 % 5 = 2.
  So, "mango" is also placed in slot 2.

Now, both "apple" and "mango" end up in **slot 2**, which is a **collision**.

### How to Handle Collisions?

There are a few methods to handle collisions when they occur:

1. **Chaining (Linked List)**:
   - In this method, instead of storing just one item in a slot, we store all items that hash to the same index in a linked list.
   - If two keys collide (hash to the same index), they are added to the linked list at that index.
   - For example, in our case, both "apple" and "mango" would be stored in a list at slot 2.

   **Example**:
   ```
   Slot 0: []
   Slot 1: []
   Slot 2: ["apple", "mango"]
   Slot 3: []
   Slot 4: []
   ```

2. **Open Addressing**:
   - Instead of adding the collided item to a list, we search for the next available slot in the hash table.
   - There are different strategies for finding the next available slot:
     - **Linear Probing**: If slot 2 is taken, check slot 3, then slot 4, and so on.
     - **Quadratic Probing**: Check slots in a quadratic pattern (e.g., 1, 4, 9 steps ahead).
     - **Double Hashing**: Use a second hash function to calculate how far to jump when a collision occurs.

   **Example of Linear Probing**:
   - "apple" hashes to slot 2.
   - "mango" hashes to slot 2, but slot 2 is already occupied, so we move to slot 3 (next slot).
   - If slot 3 is also occupied, we move to slot 4, and so on.

### Why Are Collisions a Problem?

Collisions are not a big problem if handled properly. However, if many keys end up in the same slot (because of poor hashing or a high load factor), it can slow down the operations like searching, inserting, and deleting. This happens because we have to search through a chain or probe through several slots, which takes more time.

---

### In Summary:

- A **collision** in hashing occurs when two keys have the same hash value and are mapped to the same index in the hash table.
- Collisions are a problem because they can slow down operations, but they can be handled using techniques like **chaining** (storing colliding items in a list) or **open addressing** (finding the next available slot).

I hope that clears things up! If you need further clarification, feel free to ask.