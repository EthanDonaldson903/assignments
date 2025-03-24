# Assignment 7: Linked Lists


## Task 1

**Create a linked list in C++, add nodes and delete nodes at the start of the list.**


The following code is a linked list in C++, with the requested capabilities:

```C++
#include <iostream>
using namespace std;

// Node structure
struct Node {
    int data;
    Node* next;

    Node(int value) { // Constructor
        data = value;
        next = nullptr;
    }
};

// Linked List class
class LinkedList {
private:
    Node* head;
public:
    LinkedList() { // Constructor
        head = nullptr;
    }

    // Insert node at the start
    void insertAtStart(int value) {
        Node* newNode = new Node(value);
        newNode->next = head;
        head = newNode;
    }

    // Delete node from the start
    void deleteFromStart() {
        if (head == nullptr) {
            cout << "List is empty, nothing to delete." << endl;
            return;
        }
        Node* temp = head;
        head = head->next;
        delete temp;
    }

    // Display the list
    void display() {
        Node* temp = head;
        while (temp != nullptr) {
            cout << temp->data << " -> ";
            temp = temp->next;
        }
        cout << "NULL" << endl;
    }
};

int main() {
    LinkedList list;

    list.insertAtStart(10);
    list.insertAtStart(20);
    list.insertAtStart(30);
    
    cout << "Linked List after insertions: ";
    list.display();

    list.deleteFromStart();
    cout << "Linked List after deleting from start: ";
    list.display();

    return 0;
}



```
