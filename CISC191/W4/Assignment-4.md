# Assignment 4

## Task 1

**Proof that, under the average-case scenario, the insertion sort has a time complexity of O(N2)
. Draw a clear figure and show all the operations clearly.**

See picture shown in video portion for assignment on canvas.
![image](https://github.com/user-attachments/assets/20120e5b-0083-4a2c-9549-9e7b70efdc75)



## Task 2

**At the start of the insertion sort, the index of the inspected value is set to 1. Change the index of the inspected value and verify that the total number of operations equals 20. Consider the worst-case scenario. Use N=5, where N is the number of elements.**

If we are given an array of N = 5, for this example, imagine the array is as follows :  [5, 4, 3, 2, 1] (worst case scenario)

If you were to start at any other index other than 1, in this case 2, it would still regardless take 20 operations, 10 comparisons and 10 shifts. 

2nd Element: 1 comparisons , 1 shift

3rd Element: 2 comparisons , 2 shifts

4th Element: 3 comparisons , 3 shifts

5th element: 4 comparisons , 4 shifts

These add up to 10 comparisons and 10 shifts, totaling 20 operations. 


## Task 3

**The following function returns whether or not a capital “X” is present within a string.**

```C++
function containsX(string) {
	foundX = false;
	for(let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			foundX = true; 
		}
	}
	return foundX; 
}

```


**a) What is this function’s time complexity regarding Big O Notation?**

When considering the following code in C++, the function's time complexity regarding Big O notation would be O(N). This is because, even if you find the X within the string, 
the function will still iterate through the rest of the String to check all of the characters, giving us O(N) complexity.

**(b) Then, modify the code to improve the algorithm’s efficiency for best- and average-case scenarios.**

A way to improve the algorithm's efficiency for best and average case scenarios would be to make it so that the function terminated once the X was found, thus stopping the function when X is found and not at the end of the String. This would look something like the following:

``` C++

function containsX(string) {
	for (let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			return true;  // Exit immediately when "X" is found
		}
	}
	return false; 
}


```

This would effectively get rid of the foundX variable, and simply return the boolean value immediately upon finding it, which would cut out the excess iteration from the original code.
