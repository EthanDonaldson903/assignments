# Activity 6 Stacks and Queues

## Task 1

**Using Figure 17 as a model, in the book Data Structures in C++, illustrate the result of each operation in the sequence PUSH(S,4), PUSH(S,1), PUSH(S,3), POP(S), PUSH(S,8), and POP(S) on an initially empty stack S stored in array S[1..6]. Code is not required. 3 pts**

Assuming the steps above are iterated through in the order they are provided in, the results in the new array "stack" can be given as follows


Step 1:   
Stack = [4, _, _, _, _, _,]  
S.top = 1



Step 2:  
Stack = [4, 1, _, _, _, _,]  
S.top = 2  



Step 3:   
Stack = [4, 1, 3, _, _, _]  
S.top = 3




Step 4:   
Stack: [4, 1, _, _, _, _]  
S.top = 2  



Step 5:  
Stack: [4, 1, 8, _, _, _]  
S.top = 3  


Step 6:  
Stack: [4, 1, _, _, _, _]  
S.top = 2


## Task 2


**Using Figure 18 as a model, in the book Data Structures in C++, illustrate the result of each operation in the sequence ENQUEUE(Q,4), ENQUEUE(Q,1), ENQUEUE(Q,3), DEQUEUE(Q), ENQUEUE(Q,8), and DEQUEUE(Q) on an initially empty queue Q stored in array Q[1..6]. Code is not required. 3 pts**

The following results in an empty queue Q would be stored as the following:


Step 1:  
Queue: [4, _, _, _, _, _]  
Q.head = 1, Q.tail = 1


Step 2:  
Queue: [4, 1, _, _, _, _]  
Q.head = 1, Q.tail = 2


Step 3:  
Queue: [4, 1, 3, _, _, _]  
Q.head = 1, Q.tail = 3


Step 4:  
Queue: [_, 1, 3, _, _, _]  
Q.head = 2, Q.head = 3


Step 5:  
Queue: [_, 1, 3, 8, _, _]  
Q.head = 2, Q.tail = 4


Step 6:  
Queue: [_, _, 3, 8, _ , _]  
Q.head = 3, Q.tail = 4


## Task 3

**Rewrite ENQUEUE and DEQUEUE to detect underflow and overflow of a queue. (see Listings 4 & 5 in the book). Code is not required. 1 pt**


Rewritten ENQUEUE CODE:

```C++
if (Q.tail + 1 == Q.head) OR (Q.tail == Q.length AND Q.head == 1)  
    Report "Queue Overflow" and exit  
else  
    Q[Q.tail] = x  
    if Q.tail == Q.length  
        Q.tail = 1  
    else  
        Q.tail = Q.tail + 1  

```



Rewritten DEQUEUE CODE:

```C++
if Q.head == Q.tail  
    Report "Queue Underflow" and exit  
else  
    x = Q[Q.head]  
    if Q.head == Q.length  
        Q.head = 1  
    else  
        Q.head = Q.head + 1  
    return x  
```


## Task 4

**A stack allows insertion and deletion of elements at only end, and a queue allows insertion at one end and deletion at the other end, a deque (double-ended queue) allows insertion and deletion at both ends. Write four O(1)-time procedures to insert elements into and delete elements from both ends of a deque implemented by an array. Code is not required. 3 pts**


Given that we need 4 procedures of O(1)-time complexities, the following can be the named procedures:

1. INSERT-FRONT(Q,x)  
2. INSERT-REAR(Q,x)  
3. DELETE-FRONT(Q)  
4. DELETE-REAR(Q)  



And the following code (psuedo-code) for these are as follows:  


Procedure 1:  

```C++
if (Q.front == 1 AND Q.rear == Q.length) OR (Q.front == Q.rear + 1)  
    Report "Deque Overflow" and exit  
else if Q.front == 1  
    Q.front = Q.length  
else  
    Q.front = Q.front - 1  
Q[Q.front] = x  
```


Procedure 2:  

```C++
if (Q.front == 1 AND Q.rear == Q.length) OR (Q.front == Q.rear + 1)  
    Report "Deque Overflow" and exit  
else if Q.rear == Q.length  
    Q.rear = 1  
else  
    Q.rear = Q.rear + 1  
Q[Q.rear] = x  
```


Procedure 3:

```C++
if Q.front == -1  
    Report "Deque Underflow" and exit  
x = Q[Q.front]  
if Q.front == Q.rear  
    Q.front = Q.rear = -1  (Deque is now empty)  
else if Q.front == Q.length  
    Q.front = 1  
else  
    Q.front = Q.front + 1  
return x  
```


Procedure 4:

```C++
if Q.rear == -1  
    Report "Deque Underflow" and exit  
x = Q[Q.rear]  
if Q.front == Q.rear  
    Q.front = Q.rear = -1  (Deque is now empty)  
else if Q.rear == 1  
    Q.rear = Q.length  
else  
    Q.rear = Q.rear - 1  
return x  
```


