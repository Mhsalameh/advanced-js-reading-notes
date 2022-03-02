
# Linear Complexity Growth
- Big O(oh) notation is used to describe the efficiency of an algorithm or function. This efficiency is evaluated based on 2 factors:
    1. Running Time (also known as time efficiency / complexity)
    2. Memory Space (also known as space efficiency / complexity)
- Big O’s role in algorithm efficiency is to describe the Worst Case of efficiency an algorithm can have in performing it’s job. It specifically looks at the factors mentioned above, which we often refer to as Space and Time.
- In order to analyze these limiting factors, we should consider 4 Key Areas for analysis:
    1. Input size
    2. Units of Measurement
    3. Orders of Growth
    4. Best case, Worst case, and Average case.

## Input size:
- Input Size refers to the size of the parameter values that are read by the algorithm. This does not simply refer to the number of parameters an algorithm reads, but takes into account the size of each parameter value as well.
- We will use the letter n to refer to the Input Size value.

## Units of Measurement
- To evaluate a function for Time and Space complexity, we need a way to measure each of these factors.
- for time : 
    1. The time in milliseconds from the start of a function execution until it ends.
    2. The number of operations that are executed.
    3. The number of “Basic Operations” that are executed.
- for Space (memory space): 
    1. The amount of space needed to hold the code for the algorithm.
    2. The amount of space needed to hold the input data.
    3. The amount of space needed for the output data.
    4. The amount of space needed to hold working space during the calculation.

## Linear Growth complexity:
- If an algorithm has Linear Complexity, the size of our inputs ‘n’ will directly determine the amount of Memory Space used and Running Time length. This is a very common efficiency and is usually used to denote functions with loops, or often algorithms that use recursion.

# Linked List
## What is a Linked List?
A Linked List is a sequence of Nodes that are connected/linked to each other. The most defining feature of a Linked List is that each Node references the next Node in the link.
<br/>
There are two types of Linked List - Singly and Doubly. We will be implementing a Singly Linked List in this implementation.
![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList1.PNG)

## What’s a Linked List, Anyway? [Part 1]
- Linear Data Structure:
    - If we really want to understand the basics of linked lists, it’s important that we talk about what type of data structure they are.
One characteristic of linked lists is that they are linear data structures, which means that there is a sequence and an order to how they are constructed and traversed. We can think of a linear data structure like a game of hopscotch: in order to get to the end of the list, we have to go through all of the items in the list in order, or sequentially. Linear structures, however, are the opposite of non-linear structures. In non-linear data structures, items don’t have to be arranged in order, which means that we could traverse the data structure non-sequentially.
![](https://miro.medium.com/max/1400/1*Xokk6XOjWyIGCBujkJsCzQ.jpeg)<br/>
- Memory management
    - when a linked list is born, it doesn’t need 7 bytes of memory all in one place. One byte could live somewhere, while the next byte could be stored in another place in memory altogether! Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.
![](https://miro.medium.com/max/1400/1*G43FVT5xJ1n1QDKVNZUxXQ.jpeg)