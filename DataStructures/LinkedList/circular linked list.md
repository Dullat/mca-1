A **circular linked list** is a variation of a linked list where the last node points back to the first node, forming a circle. This allows for continuous traversal of the list without needing to reach a `null` reference.

### Key Features

1. **Circular Structure**: In a circular linked list, there is no null reference at the end. Instead, the last node's `next` pointer points back to the head of the list.
   
2. **Single or Doubly Circular Linked List**: 
   - **Singly Circular Linked List**: Each node has a pointer to the next node.
   - [[doubly circular linked list]]: Each node has pointers to both the next and previous nodes, with the last node pointing to the head and the head pointing back to the last node.

### Node Structure

```plaintext
Node:
    data
    next
```

### Circular Linked List Structure

```plaintext
CircularLinkedList:
    head
```

### Basic Operations

#### 1. Insertion

- **At the Beginning**:

```plaintext
function insertAtBeginning(list, newData):
    newNode = new Node(newData)
    
    if list.head is null:  // List is empty
        list.head = newNode
        newNode.next = newNode  // Points to itself
    else:
        newNode.next = list.head
        current = list.head
        while current.next is not list.head:
            current = current.next
        current.next = newNode
        list.head = newNode
```

- **At the End**:

```plaintext
function insertAtEnd(list, newData):
    newNode = new Node(newData)
    
    if list.head is null:  // List is empty
        list.head = newNode
        newNode.next = newNode  // Points to itself
    else:
        current = list.head
        while current.next is not list.head:
            current = current.next
        current.next = newNode
        newNode.next = list.head  // Points back to head
```

#### 2. Traversal

Traversal involves continuously visiting nodes starting from the head until you loop back to the head:

```plaintext
function traverse(list):
    if list.head is null:
        return
    
    current = list.head
    do:
        print(current.data)
        current = current.next
    while current is not list.head
```

### Example Usage

```plaintext
function main():
    list = new CircularLinkedList()
    
    insertAtEnd(list, data1)
    insertAtEnd(list, data2)
    insertAtBeginning(list, data3)
    
    print("Traversal of circular linked list:")
    traverse(list)
```

### Summary
- A circular linked list connects the last node back to the first, allowing for infinite traversal.
- Basic operations include insertion at the beginning and end, and traversal.
- It can be implemented as either a singly or doubly circular linked list.