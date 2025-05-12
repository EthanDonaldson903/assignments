# Activity: Space Constraints


## Task 1

**The following exercises provide you with the opportunity to practice with space constraints.
Following is the 'Word Builder' algorithm. Describe its space complexity in terms of Big O.**

```C++
function wordBuilder(array) { 
		let collection = [];
		for(let i = 0; i < array.length; i++) { 
				for(let j = 0; j < array.length; j++) {
						if (i !== j) {
								collection.push(array[i] + array[j]);
						}
				}
		}
		return collection; 
}
```

The space complexity of the following will be O(N^2), as each pair of i and j where i !== j will push a new string into the collection, resulting in n*(n-1) which is roughly N^2 complexity.

## Task 2

**Following is a function that reverses an array. Describe its space complexity in terms of Big O:**

```C++
function reverse(array) { 
		let newArray = [];
		for (let i = array.length - 1; i >= 0; i--) { 
				newArray.push(array[i]);
		}
		return newArray;
}
```

The space complexity of the above is O(N), as it will create an array the same size as the input.


## Task 3

**Create a new function to reverse an array that takes up just O(1) extra space.**

```C++
#include <vector>
#include <algorithm> // for swap
using namespace std;

vector<int> reverseInPlace(vector<int>& array) {
    int left = 0;
    int right = array.size() - 1;

    while (left < right) {
        swap(array[left], array[right]);
        left++;
        right--;
    }

    return array;
}
```


## Task 4

**Following are three different implementations of a function that accepts an array of numbers and returns an array containing those numbers multiplied by 2. For example, if the input is [5, 4, 3, 2, 1], the output will be [10, 8, 6, 4, 2].**

```C++
function doubleArray1(array) { 
	let newArray = [];

	for(let i = 0; i < array.length; i++) { 
		newArray.push(array[i] * 2);
	}
	return newArray; 
}


function doubleArray2(array) {
	for(let i = 0; i < array.length; i++) {
  	array[i] *= 2;
  }
	return array; 
}


function doubleArray3(array, index=0) { 
	if (index >= array.length) { return; }
  array[index] *= 2;
  doubleArray3(array, index + 1);
	return array; 
}
```


Version	     Time complexity	Space complexity     
Version #1	     O(N)              O(N)   
Version #2	     O(N)              O(1)   
Version #3	     O(N)              O(N)   
