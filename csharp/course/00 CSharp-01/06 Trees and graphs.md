Certainly! In .NET Core (and later .NET 5+), you can implement trees and graphs using custom classes or third-party libraries. Here's a basic overview of how you can implement trees and graphs in C#:

### Trees
A tree is a hierarchical data structure consisting of nodes connected by edges. Each node has a parent (except the root) and zero or more children.

```csharp
using System;
using System.Collections.Generic;

public class TreeNode<T>
{
    public T Data { get; set; }
    public List<TreeNode<T>> Children { get; set; }

    public TreeNode(T data)
    {
        Data = data;
        Children = new List<TreeNode<T>>();
    }

    public void AddChild(TreeNode<T> child)
    {
        Children.Add(child);
    }
}

public class Tree<T>
{
    public TreeNode<T> Root { get; set; }

    public Tree(T rootData)
    {
        Root = new TreeNode<T>(rootData);
    }
}

class Program
{
    static void Main()
    {
        Tree<int> tree = new Tree<int>(1);
        TreeNode<int> node2 = new TreeNode<int>(2);
        TreeNode<int> node3 = new TreeNode<int>(3);
        tree.Root.AddChild(node2);
        tree.Root.AddChild(node3);
    }
}
```

### Graphs
A graph is a collection of nodes (vertices) and edges between them. Graphs can be directed or undirected, and edges can have weights.

```csharp
using System;
using System.Collections.Generic;

public class Graph<T>
{
    public Dictionary<T, List<T>> AdjacencyList { get; set; }

    public Graph()
    {
        AdjacencyList = new Dictionary<T, List<T>>();
    }

    public void AddVertex(T vertex)
    {
        AdjacencyList[vertex] = new List<T>();
    }

    public void AddEdge(T source, T destination)
    {
        if (!AdjacencyList.ContainsKey(source))
            AddVertex(source);

        if (!AdjacencyList.ContainsKey(destination))
            AddVertex(destination);

        AdjacencyList[source].Add(destination);
        // For undirected graph, you would add destination -> source as well
    }
}

class Program
{
    static void Main()
    {
        Graph<int> graph = new Graph<int>();
        graph.AddEdge(1, 2);
        graph.AddEdge(1, 3);
        graph.AddEdge(2, 3);
    }
}
```

These are basic examples of implementing trees and graphs in .NET Core C#. Depending on your specific requirements, you might need to add more functionality to these classes, such as traversal algorithms, searching, or specific properties. Let me know if you need further clarification or more examples!