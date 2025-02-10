# Array Data Structure Assignment 1



## Task 1

To create an array of 100 elements within C++, assuming the array is named "array" it would be as follows:


```C++
int array[100];

```

Where the int array would be initialized, but not have any values assigned to the values within the 100 value long array.


## Task 2

To then find the size of each element of the array, you would use the following code:

```C++
int main() {
  int x;
    int array[100];
    std::cout <<  sizeof(array[x]) << std::endl;
    return 0;
}
```

This code would be able to find the size of any variable x of the given array, according to whatever index you set x equal to. 
You can also simply create a for loop to find all of the lengths of each value, if you were to find all of them.

## Task 3

**Reading**: In the case that you are attempting to read the values of the array, it would take the complexity of O(1), or one read, as you would only be looking for one the value of one index. 



**Searching for a value**: In the case that you are looking for a value that is not within the array, and you are unaware of its location or if it exists, it would take around O(N) complexity, or N amounts of steps to search for the value, which in this case would be 100.

**Insertion at the beginning of an array:** In the case that you want to insert a value at the beginning of an array, it would take O(N), which would be 100 steps, as you would have to move each value to the right once so you can make space for the new value.

**Insertion at the end of an array:** If you are trying to insert a value at the end of an array, it would take O(N), as if it was a fixed array you would have to make a new array of 1 size greater, copy the values from the first to the second using ideally a for loop, and then add the last value at the end.

**Deletion at the beginning of an array:** It would take O(N) steps to delete the first value of an array, as you would have to move each value to the left once, to appropriately fill the space that the deletion had done.

**Deletion at the end of an array:** It would take O(1) steps to delete the last value of an array, as you would not have to perform any shifting of elements within the array.

## Task 4

If you are given an array, and you are trying to count how many times the word "apple", or any other specific value occured within the array, it would take O(N) amount of steps to complete. This is because it would require you to sort through each value within the integer, and check with an if statement to see if the value stored at the index is the same as what you are looking for.

## Task 5

After researching to find the memory address of an array, the code goes as follows:

```C++


int main() {
    int array[100];
    std::cout << "Memory address of array: " << &array << std::endl;
    return 0;
}

```

Where it would return the address of the array that we created earlier, using the & operator.


 
