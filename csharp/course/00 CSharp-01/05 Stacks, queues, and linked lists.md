Certainly! In .NET Core (and later .NET 5+), you have built-in implementations for stacks, queues, and linked lists in the `System.Collections.Generic` namespace. Here's how you can use them:

### Stacks
A stack is a last-in, first-out (LIFO) collection.

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Stack<int> stack = new Stack<int>();

        // Pushing elements onto the stack
        stack.Push(1);
        stack.Push(2);
        stack.Push(3);

        // Popping elements from the stack
        while (stack.Count > 0)
        {
            int popped = stack.Pop();
            Console.WriteLine($"Popped: {popped}");
        }
    }
}
```

### Queues
A queue is a first-in, first-out (FIFO) collection.

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Queue<int> queue = new Queue<int>();

        // Enqueuing elements into the queue
        queue.Enqueue(1);
        queue.Enqueue(2);
        queue.Enqueue(3);

        // Dequeuing elements from the queue
        while (queue.Count > 0)
        {
            int dequeued = queue.Dequeue();
            Console.WriteLine($"Dequeued: {dequeued}");
        }
    }
}
```

### Linked Lists
A linked list is a linear collection of elements where each element points to the next one.

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        LinkedList<int> linkedList = new LinkedList<int>();

        // Adding elements to the linked list
        linkedList.AddLast(1);
        linkedList.AddLast(2);
        linkedList.AddLast(3);

        // Iterating through the linked list
        foreach (var item in linkedList)
        {
            Console.WriteLine($"Item: {item}");
        }
    }
}
```

These are basic examples of using stacks, queues, and linked lists in .NET Core C#. You can perform various operations on them like adding, removing, searching, etc. Each collection provides methods for these operations, and you can also iterate over them using foreach loops. Let me know if you need further clarification or more examples!