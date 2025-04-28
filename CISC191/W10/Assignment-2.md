# Graphs : Assignment 2

## Task 1


**1. Explain with the help of an example "Why Dijkstra's algorithm fails on negative weights".**


Dijkstra's alogrithm fails on negative weights because it assumes that once a node's shortest distance is found, it will never be updated again. However, this assumption holds true only when all edge weights are non-negative, as there may exist a shorter path, but it will never be found.

![image](https://github.com/user-attachments/assets/dbd749bf-eacc-4919-b52c-c7fc7c7fb68c)



Observing the example graph above, one can see that the path from A to B is 4, while the path from A to C is 1, and the path from C to B is -2, thus making the path from A to C to B -1. This is infact a shorter path than that of A to B, but it would not be considered in the path that Dijkstra's algorithm would choose. This is because the algorithm would finalize the path from A to B as the shortest, and not check the other paths.
