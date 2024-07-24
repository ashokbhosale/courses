Performance profiling in .NET Core C# involves analyzing the execution time and resource usage of your application to identify bottlenecks and optimize performance. Let's explore how to perform performance profiling with examples:

### Using Visual Studio Profiler

1. **Run Profiler**
   - Open your .NET Core C# project in Visual Studio.
   - Navigate to "Debug" -> "Performance Profiler" -> "Performance Explorer".
   - Choose the profiling method (e.g., CPU Sampling, Memory Usage, etc.).

2. **Start Profiling Session**
   - Click on the "Start" button to start the profiling session.
   - Perform actions in your application to capture performance data.

3. **Analyze Results**
   - After the profiling session, analyze the captured data to identify performance bottlenecks.
   - Visual Studio provides various views and tools to analyze CPU usage, memory allocation, function timings, and more.

### Using BenchmarkDotNet

BenchmarkDotNet is a powerful library for benchmarking and performance testing in .NET. Here's how to use it:

1. **Install BenchmarkDotNet**
   - Install the BenchmarkDotNet NuGet package in your project.
   ```bash
   dotnet add package BenchmarkDotNet
   ```

2. **Write Benchmarks**
   - Write benchmark methods using the `[Benchmark]` attribute.
   ```csharp
   using BenchmarkDotNet.Attributes;

   public class MyBenchmark
   {
       [Benchmark]
       public void MyMethod()
       {
           // Code to benchmark
       }
   }
   ```

3. **Run Benchmarks**
   - Run the benchmarks using the BenchmarkDotNet runner.
   ```bash
   dotnet run -c Release --filter *MyBenchmark*
   ```

4. **Analyze Results**
   - Analyze the benchmark results to identify performance characteristics and potential optimizations.

### Using PerfView

PerfView is a performance analysis tool provided by Microsoft. Here's how to use it:

1. **Download and Install PerfView**
   - Download and install PerfView from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

2. **Collect Data**
   - Launch PerfView and start a new profiling session.
   - Capture data while running your .NET Core C# application.

3. **Analyze Results**
   - After capturing data, PerfView provides various views and tools to analyze CPU usage, memory allocation, garbage collection, and more.

### Example BenchmarkDotNet Benchmark

```csharp
using BenchmarkDotNet.Attributes;
using BenchmarkDotNet.Running;

public class MyBenchmark
{
    [Benchmark]
    public void MyMethod()
    {
        // Code to benchmark
    }
}

class Program
{
    static void Main(string[] args)
    {
        var summary = BenchmarkRunner.Run<MyBenchmark>();
    }
}
```

By using performance profiling tools like Visual Studio Profiler, BenchmarkDotNet, and PerfView, you can analyze the performance of your .NET Core C# application, identify performance bottlenecks, and optimize critical sections of code to improve overall performance.