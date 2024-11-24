https://www.javatpoint.com/avl-tree

Rotations are fundamental operations in AVL trees that help maintain the tree's balance after insertions and deletions. When the balance factor of any node becomes less than -1 or greater than +1, rotations are used to restore balance. There are four types of rotations: Right Rotation, Left Rotation, Left-Right Rotation, and Right-Left Rotation. Let’s explore each one in detail.

### 1. Right Rotation (LL Rotation)

**Use Case**: This rotation is used when a node is added to the left subtree of the left child, causing a left-heavy imbalance.

**Diagram**:

Before Right Rotation:

```
      z
     /
    y
   /
  x
```

**Steps**:
- The subtree rooted at `y` becomes the new root.
- `z` becomes the right child of `y`.
- `T2` (the right subtree of `x`) becomes the left child of `z`.

After Right Rotation:

```
      y
     / \
    x   z
```

### 2. Left Rotation (RR Rotation)

**Use Case**: This rotation is used when a node is added to the right subtree of the right child, causing a right-heavy imbalance.

**Diagram**:

Before Left Rotation:

```
    z
     \
      y
       \
        x
```

**Steps**:
- The subtree rooted at `y` becomes the new root.
- `z` becomes the left child of `y`.
- `T2` (the left subtree of `y`) becomes the right child of `z`.

After Left Rotation:

```
      y
     / \
    z   x
```

### 3. Left-Right Rotation (LR Rotation)

**Use Case**: This rotation is used when a node is added to the right subtree of the left child, causing a left-right imbalance.

**Diagram**:

Before Left-Right Rotation:

```
      z
     /
    y
     \
      x
```

**Steps**:
1. First, perform a left rotation on `y` to balance the left subtree.

Intermediate After Left Rotation on `y`:

```
      z
     /
    x
   /
  y
```

2. Then, perform a right rotation on `z`.

After Left-Right Rotation:

```
      x
     / \
    y   z
```

### 4. Right-Left Rotation (RL Rotation)

**Use Case**: This rotation is used when a node is added to the left subtree of the right child, causing a right-left imbalance.

**Diagram**:

Before Right-Left Rotation:

```
    z
     \
      y
     /
    x
```

**Steps**:
1. First, perform a right rotation on `y` to balance the right subtree.

Intermediate After Right Rotation on `y`:

```
    z
     \
      x
       \
        y
```

2. Then, perform a left rotation on `z`.

After Right-Left Rotation:

```
      x
     / \
    z   y
```

### Summary

- **Right Rotation (LL)**: Used for left-left imbalances.
- **Left Rotation (RR)**: Used for right-right imbalances.
- **Left-Right Rotation (LR)**: Used for left-right imbalances.
- **Right-Left Rotation (RL)**: Used for right-left imbalances.

By performing these rotations, AVL trees maintain a balanced structure, ensuring that the height remains logarithmic relative to the number of nodes. This leads to efficient search, insertion, and deletion operations, typically in \(O(\log n)\) time. If you have any further questions or need clarification, feel free to ask!


---

## deletion

Deletion in an AVL tree involves a few steps similar to deletion in a regular binary search tree, but with the added complexity of maintaining the AVL balance property. Here’s a detailed breakdown of the deletion process in an AVL tree.

### Steps for Deletion in an AVL Tree

1. **Perform Standard BST Deletion**:
   - Find the node to be deleted just like you would in a standard binary search tree.
   - If the node has:
     - **No children** (leaf node): Simply remove it.
     - **One child**: Remove the node and link its parent directly to its child.
     - **Two children**: 
       - Find the in-order predecessor or successor (maximum in the left subtree or minimum in the right subtree).
       - Replace the value of the node to be deleted with the value of the predecessor/successor.
       - Delete the predecessor/successor node, which will have at most one child.

2. **Update Heights**:
   - After the deletion, update the heights of the ancestor nodes of the deleted node, as the tree structure has changed.

3. **Check Balance Factors**:
   - Check the balance factor of each ancestor node after the deletion. The balance factor is calculated as:
     \[
     \text{Balance Factor} = \text{Height of Left Subtree} - \text{Height of Right Subtree}
     \]
   - If any balance factor is less than -1 or greater than +1, the tree is unbalanced.

4. **Perform Rotations**:
   - Depending on the balance factor of the unbalanced nodes, perform the necessary rotations to restore balance. There are four cases to consider:
     - **Left-Left Case (LL)**: Perform a right rotation.
     - **Right-Right Case (RR)**: Perform a left rotation.
     - **Left-Right Case (LR)**: Perform a left rotation on the left child followed by a right rotation.
     - **Right-Left Case (RL)**: Perform a right rotation on the right child followed by a left rotation.

### Example of Deletion in an AVL Tree

Let’s illustrate the deletion process with an example.

#### Initial AVL Tree

```
      30
     /  \
   20    40
  / \      \
 10  25    50
```

#### Deleting Node 20

1. **Standard BST Deletion**: Node `20` has two children (10 and 25). We can replace it with its in-order successor (25), and then delete the original node `25`.

After replacing `20` with `25`, the tree looks like this:

```
      30
     /  \
   25    40
  /      \
 10      50
```

Now we need to delete the original node `25`.

2. **Delete Node 25**: Node `25` has one child (10). We remove `25`, linking `30` directly to `10`.

After deletion, the tree looks like this:

```
      30
     /  \
   10    40
        \
        50
```

3. **Update Heights**: Update the heights of affected nodes. 

4. **Check Balance Factors**: The balance factors for the nodes will now be checked. In this case, `30` has a balance factor of 1 (left subtree height 1, right subtree height 2), which is within the acceptable range.

No rotations are needed in this case.

### Summary

- **Deletion** in an AVL tree involves standard BST deletion logic, followed by updating heights and checking balance factors.
- If the tree becomes unbalanced, appropriate rotations are performed to restore balance.
- The entire process ensures that the AVL tree remains balanced, maintaining efficient performance for future operations.

If you have further questions or need more details on any aspect, feel free to ask!