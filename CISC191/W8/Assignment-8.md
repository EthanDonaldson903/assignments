# Binary Search Trees Assignment


## Task 1

**Imagine you were to take an empty binary search tree and insert the following sequence of numbers in this order: [1, 5, 9, 2, 4, 10, 6, 3, 8]. Draw a diagram showing what the binary search tree would look like. Remember, the numbers are being inserted in the order presented here.**

![image](https://github.com/user-attachments/assets/e6cb475a-8113-4454-8f73-554f58fd7a6c)



## Task 2

**If a well-balanced binary search tree contains 1,000 values, what is the maximum number of steps it would take to search for a value within it?**



Since a well-balanced binary search tree has a height of log2(n), that means the maximum number of steps a binary search tree of height n = 1000 would take, at worst 10 steps.


## Task 3

**Write an algorithm that finds the greatest value within a binary search tree.**




The following code is this algorithm, but in psudeocode rather than in C++




```C++
Node* findMax(Node* root) {
    if (root == nullptr) return nullptr; // Empty tree case
    while (root->right != nullptr) {
        root = root->right;
    }
    return root; // The maximum value node
}
```



## Task 4


**Write a code in C++ using the same array mentioned in #1 and implement a binary search tree. Only insertion operation is required.**



```C++
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
    
    Node(int value) {
        data = value;
        left = right = nullptr;
    }
};

class BST {
public:
    Node* root;
    
    BST() { root = nullptr; }
    
    void insert(int value) {
        root = insertRec(root, value);
    }
    
    void inorder(Node* node) {
        if (node == nullptr) return;
        inorder(node->left);
        cout << node->data << " ";
        inorder(node->right);
    }
    
    void display() {
        inorder(root);
        cout << endl;
    }

private:
    Node* insertRec(Node* node, int value) {
        if (node == nullptr) return new Node(value);
        
        if (value < node->data) 
            node->left = insertRec(node->left, value);
        else 
            node->right = insertRec(node->right, value);
        
        return node;
    }
};

int main() {
    BST tree;
    int values[] = {1, 5, 9, 2, 4, 10, 6, 3, 8};
    for (int value : values) {
        tree.insert(value);
    }

    cout << "Inorder Traversal of BST: ";
    tree.display();

    return 0;
}
```
