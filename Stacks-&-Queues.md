# Stacks and Queues

![img](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Stack-Queue.png)

# What is a stack?

A stack : is a data structure that consists of Nodes. Each Node references the next Node in the stack, but does not reference its previous.

## stack concept

- `FILO ` ==> First In Last Out

  This means that the first item added in the stack will be the last item popped out of the stack.

- `LIFO` ==> Last In First Out

  This means that the last item added to the stack will be the first item popped out of the stack.

## Common terminology for a stack is :

1. `Push` - Nodes or items that are put into the stack are pushed<br>
   **Steps**

   - Have a node you want to add
   - Assign the next property to reference the same node that top is referencing. Top is the node on top of the stack
   - The new node is added to the stack but you need to indicate that it is now the first node. Re-assign our reference top to the new node then you're done!

2. `Pop` - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.<br>
   **Steps**

   - Create a reference named temp that points to the same node that top points to
   - Reassign top to the value of the next node
   - Clear out the next property in the temp node then remove it
   - Return the value of the temp node that was popped

3. `Top` - This is the top of the stack. <br>

4. `Peek` - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.<br>

5. `IsEmpty` - returns true when stack is empty otherwise returns false.<br>

### Stack Visualization

**PUSH**

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/stack1.PNG)

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/pushStack1.PNG)

assign the next property of Node 5 to reference the same Node that top is referencing: Node 4

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/pushStack2.PNG)

re-assign our reference top to the newly added Node, Node 5.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/pushStack3.PNG)

## Stack pseudoCode for :

1. pseudoCode to `push` O(1) a value onto a stack:

```
ALOGORITHM push(value)
// INPUT <-- value to add, wrapped in Node internally
// OUTPUT <-- none
   node = new Node(value)
   node.next <-- Top
   top <-- Node
```

2. pseudocode for a `pop` O(1) :

```
ALGORITHM pop()
// INPUT <-- No input
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   Node temp <-- top
   top <-- top.next
   temp.next <-- null
   return temp.value
```

3. pseudocode for a `peek` O(1) :

```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   return top.value
```

4. pseudocode for `isEmpty` O(1) :

```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return top = NULL
```

# What is a Queue

Common terminology for a queue is :

1. Enqueue - Nodes or items that are added to the queue. <br>
2. Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.<br>
3. Front - This is the front/first Node of the queue.<br>
4. Rear - This is the rear/last Node of the queue.<br>
5. Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is 6-empty an exception will be raised.<br>
6. IsEmpty - returns true when queue is empty otherwise returns false.<br>

## Queues follow these concepts:

`FIFO` ==> First In First Out

This means that the first item in the queue will be the first item out of the queue.

`LILO` ==> Last In Last Out

This means that the last item in the queue will be the last item out of the queue.

## Enqueue :

When you add an item to a queue, you use the enqueue action. This is done with an O(1) operation in time because it does not matter how many other items live in the queue (n); it takes the same amount of time to perform the operation.

**Steps**

1. Change the next property of the rear node to point to the new node being added. Use rear.next
2. Re-assign the rear reference to point to the new node and you're done.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Enqueue1.PNG)

change the next property of Node 4 to point to the Node we are adding.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Enqueue2.PNG)

re-assign the rear reference to point to Node 5

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Enqueue3.PNG)

### pseudocode for the `enqueue` method:

```
ALGORITHM enqueue(value)
// INPUT <-- value to add to queue (will be wrapped in Node internally)
// OUTPUT <-- none
   node = new Node(value)
   rear.next <-- node
   rear <-- node
```

## Dequeue :

create a temporary reference type named temp and have it point to the same Node that front is pointing too.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Dequeue1.PNG)

re-assign front to the next value that the Node front is referencing

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Dequeue2.PNG)

re-assign the next property on the temp Node to null
![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Dequeue3.PNG)

**Steps**

- Made the front node have a temporary reference of temp.
- Re-assign front to the next node in the queue
- Reassign the next property on the temp node to be null. You have to properly clear unnecessary references
- Return the value of the temp node that was removed

### pseudocode for the `dequeue` method:

```
ALGORITHM dequeue()
// INPUT <-- none
// OUTPUT <-- value of the removed Node
// EXCEPTION if queue is empty

   Node temp <-- front
   front <-- front.next
   temp.next <-- null

   return temp.value
```

### pseudocode for a `peek` :

```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of the front Node in Queue
// EXCEPTION if Queue is empty

   return front.value
```

### pseudocode for `isEmpty` :

```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return front = NULL
```

# References :

- [Stacks and Queues](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)
