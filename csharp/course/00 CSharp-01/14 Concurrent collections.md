In .NET Core (and later .NET 5+), concurrent collections provide thread-safe alternatives to traditional collections when working with multiple threads. They ensure that operations such as adding, removing, or modifying elements can be safely performed in a multi-threaded environment without the need for explicit locking mechanisms. Here are some concurrent collections available in .NET Core C#:

### ConcurrentQueue<T>
`ConcurrentQueue<T>` provides a thread-safe FIFO (First-In-First-Out) collection.

```csharp
using System.Collections.Concurrent;

ConcurrentQueue<int> queue = new ConcurrentQueue<int>();

queue.Enqueue(1);
queue.Enqueue(2);
queue.Enqueue(3);

int result;
if (queue.TryDequeue(out result))
{
    Console.WriteLine($"Dequeued: {result}"); // Output: Dequeued: 1
}
```

### ConcurrentStack<T>
`ConcurrentStack<T>` provides a thread-safe LIFO (Last-In-First-Out) collection.

```csharp
using System.Collections.Concurrent;

ConcurrentStack<int> stack = new ConcurrentStack<int>();

stack.Push(1);
stack.Push(2);
stack.Push(3);

int result;
if (stack.TryPop(out result))
{
    Console.WriteLine($"Popped: {result}"); // Output: Popped: 3
}
```

### ConcurrentBag<T>
`ConcurrentBag<T>` provides a thread-safe collection that allows duplicates.

```csharp
using System.Collections.Concurrent;

ConcurrentBag<int> bag = new ConcurrentBag<int>();

bag.Add(1);
bag.Add(2);
bag.Add(3);

int result;
if (bag.TryTake(out result))
{
    Console.WriteLine($"Taken: {result}"); // Output: Taken: 3
}
```

### ConcurrentDictionary<TKey, TValue>
`ConcurrentDictionary<TKey, TValue>` provides a thread-safe dictionary.

```csharp
using System.Collections.Concurrent;

ConcurrentDictionary<string, int> dictionary = new ConcurrentDictionary<string, int>();

dictionary.TryAdd("one", 1);
dictionary.TryAdd("two", 2);
dictionary.TryAdd("three", 3);

int value;
if (dictionary.TryRemove("two", out value))
{
    Console.WriteLine($"Removed: {value}"); // Output: Removed: 2
}
```

### BlockingCollection<T>
`BlockingCollection<T>` provides a thread-safe collection with blocking operations for producer-consumer scenarios.

```csharp
using System.Collections.Concurrent;
using System.Threading.Tasks;

BlockingCollection<int> collection = new BlockingCollection<int>(boundedCapacity: 5);

Task.Run(() =>
{
    for (int i = 0; i < 10; i++)
    {
        collection.Add(i);
        Console.WriteLine($"Produced: {i}");
    }
});

Task.Run(() =>
{
    foreach (var item in collection.GetConsumingEnumerable())
    {
        Console.WriteLine($"Consumed: {item}");
    }
});
```

These concurrent collections provide efficient and thread-safe data structures for concurrent programming in .NET Core C#. They handle synchronization internally, making them suitable for scenarios involving multiple threads. Let me know if you need further clarification or more examples!