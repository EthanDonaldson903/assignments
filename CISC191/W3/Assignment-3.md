# Sorting Algorithms Assignment



## Task 1

**Use Big O Notation to describe the time complexity of an algorithm that takes 4N+16steps:**

To describe the time complexity of an algorithm that takes 4N+16 steps, we don't have to look at the constant of 16 steps. Rather, we pay attention to the 4N as the main indicator. Ignoring the constant, but paying attention to the N, 
the given time complexity of the algorithm would be **O(N)**.

## Task 2

**Use Big O Notation to describe the time complexity of an algorithm that takes 2N<sup>2</sup>**

Similarly to the last task, the constant attached to the N does not matter when dignifying its complexity. Mainly, we will look at the N with its level of exponents. In this case, as we are given 2N<sup>2</sup>, the correct complexity would be 
**O(N<sup>2</sup>)**

## Task 3

**Use Big O Notation to describe the time complexity of the following function, which returns the sum of all numbers of an array after the numbers have been doubled:**

Given the following code:

``` C++

def double_then_sum(array) 
	doubled_array = []

	array.each do |number| 
		doubled_array << number *= 2
	end

	sum = 0

	doubled_array.each do |number| 
		sum += number
	end
	return sum 
end
```

Looking at the code, you can see that the program will iterate through the array twice, once to double the values, and once to sum them. This will give us something around 2N, which as stated before would come out to **O(N)** complexity.


## Task 4

Given the following code:

``` C++
def multiple_cases(array) 
	array.each do |string|
		puts string.upcase 
		puts string.downcase 
		puts string.capitalize
	end 
end
```


When looking at the code, we can see that the function would only iterate through the array once, running the functions to each part of the array as it iterates through it. This in turn, would result in a single run through the array, which would 
be given in terms of N as an **O(N)** complexity.


## Task 5

Given the following code:

``` C++

def every_other(array) 
	array.each_with_index do |number, index|
		if index.even?
			array.each do |other_number|
            	puts number + other_number
			end 
		end
	end 
end

```

As this function iterates through the array once, and then when it encounters an index that is even, it iterates through the array again to add up the values, it would have an **O(N<sup>2</sup>)** complexity, as it must scale the whole array with each even index, after scaling through the array before that.


