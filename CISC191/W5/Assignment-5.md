# Hash Tables Assignment

## Task 1

**Assume you have a simple single-dimensional array
array = [200, 400, 100, 50, 350]**

**Linear search will take O(N). Write a code in C++/Python to improve the search operation efficiency from O(N) to $O(1).**

``` C++

#include <iostream>
#include <unordered_map>

using namespace std;

int main() {
    unordered_map<int, bool> hashTable;
    int array[] = {200, 400, 100, 50, 350};
    
    // Insert elements into the hash table
    for (int num : array) {
        hashTable[num] = true;
    }

    // Search for an element
    int searchKey = 100;
    if (hashTable.find(searchKey) != hashTable.end()) {
        cout << searchKey << " found in O(1) time." << endl;
    } else {
        cout << searchKey << " not found." << endl;
    }

    return 0;
}


```


The code above instills the use of a hash table, where each element is inserted as a boolean of true, under the value of itself, making it so the search will give whether or not the value exists in the hashtable, simplifying it into a single iteration of a command .find, making it O(1).

## Task 2

**Use C++, generate hash value of your name.**

```C++

#include <iostream>
#include <functional>

using namespace std;

int main() {
    string name = "ethan";
    size_t hashValue = hash<string>{}(name);
    
    cout << "Hash value of 'ethan': " << hashValue << endl;
    
    return 0;
}
```

## Task 3

**With the help of a figure, explain the problem that occured due to introducing a tombstone to mark the deleted cell.**

![image](https://github.com/user-attachments/assets/829cce36-2924-44fa-ba09-005836ec8729)

This diagram can help one understand the problems with introducign a tombstone to mark the deleted cell because, as you have now marked the [x] value with a tombstone, it could potentially act as an extra check when probing, and cause problems with inserting new values, as the tombstone still exists there.
