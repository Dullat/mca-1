```
#include <iostream>

// Node structure
struct Node {
    int data;
    Node* next;
};

// Function to create and insert a new node at the end
void insert(Node*& head, int value) {
    Node* newNode = new Node{value, nullptr};
    if (!head) {
        head = newNode;
    } else {
        Node* temp = head;
        while (temp->next) {
            temp = temp->next;
        }
        temp->next = newNode;
    }
}

// Function to delete a node by value
void deleteValue(Node*& head, int value) {
    if (!head) return;
    if (head->data == value) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return;
    }
    Node* current = head;
    while (current->next && current->next->data != value) {
        current = current->next;
    }
    if (current->next) {
        Node* temp = current->next;
        current->next = current->next->next;
        delete temp;
    }
}

// Function to display the list
void display(Node* head) {
    for (Node* temp = head; temp; temp = temp->next) {
        std::cout << temp->data << " -> ";
    }
    std::cout << "nullptr" << std::endl;
}

int main() {
    Node* head = nullptr;

    insert(head, 10);
    insert(head, 20);
    insert(head, 30);
    display(head);

    deleteValue(head, 20);
    display(head);
    return 0;
}

```