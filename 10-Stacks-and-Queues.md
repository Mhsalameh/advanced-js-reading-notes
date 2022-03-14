# Stacks and Queues

## What is stack

- A stack is a data structure that consists of Nodes, each node refers to the next node in the stack and doesn't refer to the previous

- stack concepts:

  - FILO : First In Last Out - This means that the first item added in the stack will be the last item popped out of the stack.
  - LIFO : Last In First Out - This means that the last item added to the stack will be the first item popped out of the stack.
  - Stack Visualization: example on how the stack looks:
    ![stack1](./assets/stack1.png)
  - As you can see, the topmost item is denoted as the top. When you push something to the stack, it becomes the new top. When you pop something from the stack, you pop the current top and set the next top as top.next

Common terminology for a stack is :

1. Push - Nodes or items that are put into the stack are pushed
2. Pop - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.
3. Top - This is the top of the stack.
4. Peek - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
5. IsEmpty - returns true when stack is empty otherwise returns false.

## What is queue?

Common terminology for a queue is

1. Enqueue - Nodes or items that are added to the queue.
2. Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
3. Front - This is the front/first Node of the queue.
4. Rear - This is the rear/last Node of the queue.
5. Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
6. IsEmpty - returns true when queue is empty otherwise returns false.

Queues follow these concepts:

- FIFO (First In First Out), This means that the first item in the queue will be the first item out of the queue.
- LILO (Last In Last Out), This means that the last item in the queue will be the last item out of the queue.
- Queue Visualization:
  Here is what a Queue looks like:
  ![queue](./08-Access-Control.md)

## Bookmarks

[Stacks and Queues](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)
