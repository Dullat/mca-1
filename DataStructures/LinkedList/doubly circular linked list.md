A **doubly circular linked list** combines the features of doubly linked lists and circular linked lists. Each node contains pointers to both the next and previous nodes, and the last node points back to the head, while the head points back to the last node.

### Node Structure

```plaintext
Node:
    data
    next
    prev
```

### Doubly Circular Linked List Structure

```plaintext
DoublyCircularLinkedList:
    head
```

### Insertion

#### 1. Insertion at the Beginning

```plaintext
function insertAtBeginning(list, newData):
    newNode = new Node(newData)

    if list.head is null:  // List is empty
        list.head = newNode
        newNode.next = newNode
        newNode.prev = newNode
    else:
        newNode.next = list.head
        newNode.prev = list.head.prev
        list.head.prev.next = newNode
        list.head.prev = newNode
        list.head = newNode
```

#### 2. Insertion at the End

```plaintext
function insertAtEnd(list, newData):
    newNode = new Node(newData)

    if list.head is null:  // List is empty
        list.head = newNode
        newNode.next = newNode
        newNode.prev = newNode
    else:
        newNode.next = list.head
        newNode.prev = list.head.prev
        list.head.prev.next = newNode
        list.head.prev = newNode
```

#### 3. Insertion at a Specific Position

```plaintext
function insertAfter(list, prevNode, newData):
    if prevNode is null:
        print("The given previous node cannot be null")
        return

    newNode = new Node(newData)
    newNode.next = prevNode.next
    newNode.prev = prevNode

    prevNode.next.prev = newNode
    prevNode.next = newNode
```

### Deletion

#### 1. Deletion of a Node

```plaintext
function deleteNode(list, nodeToDelete):
    if list.head is null or nodeToDelete is null:
        print("The list is empty or the node to delete is null")
        return

    if nodeToDelete is list.head and nodeToDelete.next is nodeToDelete:
        // Only one node in the list
        list.head = null
        return

    nodeToDelete.prev.next = nodeToDelete.next
    nodeToDelete.next.prev = nodeToDelete.prev

    if nodeToDelete is list.head:
        list.head = nodeToDelete.next  // Move head if needed
```

### Traversal

Traversal in a doubly circular linked list can be done in both forward and backward directions.

#### Forward Traversal

```plaintext
function traverseForward(list):
    if list.head is null:
        return

    current = list.head
    do:
        print(current.data)
        current = current.next
    while current is not list.head
```

#### Backward Traversal

```plaintext
function traverseBackward(list):
    if list.head is null:
        return

    current = list.head.prev  // Start from the last node
    do:
        print(current.data)
        current = current.prev
    while current is not list.head.prev
```

### Example Usage

```plaintext
function main():
    list = new DoublyCircularLinkedList()

    insertAtEnd(list, data1)
    insertAtEnd(list, data2)
    insertAtBeginning(list, data3)
    insertAfter(list, list.head, data4)  // Insert after the first node

    print("Forward Traversal:")
    traverseForward(list)

    print("Backward Traversal:")
    traverseBackward(list)

    // Deleting a node
    deleteNode(list, list.head)  // Delete the head node
```

### Summary

- **Insertion**: You can insert nodes at the beginning, end, or a specific position, adjusting pointers accordingly.
- **Deletion**: Removing nodes involves updating the previous and next pointers to maintain the circular structure.
- **Traversal**: You can traverse the list in both forward and backward directions, utilizing the `next` and `prev` pointers. 

This structure provides efficient access and manipulation of nodes in a circular fashion, making it useful for certain applications like round-robin scheduling or buffer management.