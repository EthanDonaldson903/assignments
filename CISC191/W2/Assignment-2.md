# Linear and Binary Search Assignment


### Task 1


To complete a linear search for the number 8 in the given array of [2, 4, 6, 8, 10, 12, 13], it would take exactly four steps. As the value 8 resides in the fourth spot (index = 3), the iteration would start at the index 0, and take 4 steps to reach index 3.


### Task 2


As for a binary search, it would first take the initial array, which is [2, 4, 6, 8, 10, 12, 13], then find the midpoint, adding the first index with the last index and dividing by two (0+6)/2, which in turn would give 3. This index is where 8 is located, so it would find the value 8 in 1 step.


### Task 3


In this task we are given an array of size 100,000. If we are talking in terms of binary search, it would split the array into half each time it ran, which could be represented by log2(100,000). This is approximately 16.6, which we could round to 17 steps.


### Task 4

My code for the linear and binary search is as follows:

```C++
#include <iostream>
using namespace std;

// Linear Search Function
int linearSearch(int arr[], int size, int target, int &steps) {
    for (int i = 0; i < size; i++) {
        steps++;
        if (arr[i] == target) {
            return i; // Return index if found
        }
    }
    return -1; // Not found
}

// Binary Search Function
int binarySearch(int arr[], int size, int target, int &steps) {
    int left = 0, right = size - 1;
    while (left <= right) {
        steps++;
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            return mid; // Found
        }
        else if (arr[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }
    return -1; // Not found
}

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12, 13};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 8;
    
    int linearSteps = 0, binarySteps = 0;
    
    int linearResult = linearSearch(arr, size, target, linearSteps);
    int binaryResult = binarySearch(arr, size, target, binarySteps);
    
    cout << "Linear Search Steps: " << linearSteps << endl;
    cout << "Binary Search Steps: " << binarySteps << endl;
    
    return 0;
}
```
