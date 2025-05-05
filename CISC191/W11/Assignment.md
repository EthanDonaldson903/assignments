# Recursions Assignment


## Task 1

**1. The following function prints every other number from a low number to a high number. For example, if low is 0 and high is 10, it would print:**
0  
2  
4  
6  
8  
10  

**Identify the base case in the function:**

```C++
def print_every_other(low, high)   
    return if low > high  
    puts low  
    print_every_other(low + 2, high)  
end  
```


In the program above, the base case line would be 


```C++
return if low > high
```


As this line would stop the recursion once low exceeds high.


## Task 2


**2. My kid was playing with my computer and changed my factorial function so that it computes factorial based on (n - 2) instead of (n - 1). Predict what will happen when we run factorial(10) using this function:**


```C++
def factorial(n)
    return 1 if n == 1
    return n * factorial(n - 2)
end
```


Since the function was changed from return n * factorial(n-1) to (n-2), this means that it being run will compile 10 * 8 * 6 * 4 * 2 * factorial(0). However, the base case only includes n == 1, and since the function will skip factorial(1), this will cause and infinite loop wihtin the recursion, as there is no base case.


## Task 3

**3. Following is a function in which we pass in two numbers called low and high. The function returns the sum of all the numbers from low to high. For example, if low is 1, and high is 10, the function will return the sum of all numbers from 1 to 10, which is 55. However, our code is missing the base case, and will run indefinitely! Fix the code by adding the correct base case:**

```C++
def sum(low, high)
    return high + sum(low, high - 1)
end
```


To fix this function, we need to create a base case in the recursion function, to make sure that if high = low, that we make sure that the recursion doesn't keep adding the high to the sum. To do this, we can make the code as follows:

```C++
def sum(low, high)
    return low if high == low  # base case
    return high + sum(low, high - 1)
end
```

In which this makes it to avoid adding values into the sum that are lower than the low.


## Task 4


**4. Here is an array containing both numbers as well as other arrays, which in turn contain numbers and arrays:**

```C++
array=[ 1, 
        2, 
        3,
        [4, 5, 6],
        7,
        [8,
          [9, 10, 11,
            [12, 13, 14]
          ] 
        ],
        [15, 16, 17, 18, 19,
          [20, 21, 22,
            [23, 24, 25,
              [26, 27, 29]
            ], 30, 31 
          ], 32
        ], 33 
      ]
```

**Write a recursive function that prints all the numbers (and just numbers).**


```C++
#include <iostream>
#include <vector>
#include <variant>

using namespace std;

// Define a variant that can hold either an int or a nested array
struct Node;
using Nested = variant<int, vector<Node>>;

struct Node {
    Nested value;
};

// Recursive function to print all integers
void printNumbers(const vector<Node>& array) {
    for (const auto& node : array) {
        if (holds_alternative<int>(node.value)) {
            cout << get<int>(node.value) << endl;
        } else {
            printNumbers(get<vector<Node>>(node.value)); // Recursive call
        }
    }
}
```
