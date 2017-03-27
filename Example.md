# Example

Description about what the code does and what it helps with. 

## Use case

When to use this. (Or when to avoid using it.)

## Proof of concept

```
// Core functionallity code that shows how it works.
// PS: This step can be skipped if the implementation is self explaining.
```

## Implementation

```
// Quality implementation with proper null checks, etc ...
```

## Benchmark

```
// Result of the implemented benchmark.

    Method |        Mean |    StdErr |    StdDev | Allocated |
---------- |------------ |---------- |---------- |---------- |
 Optimized |   2.6614 ns | 0.0451 ns | 0.2592 ns |       0 B |
   Default | 154.4741 ns | 1.4732 ns | 5.7056 ns |      20 B |
```

```
// Benchmark implementation so others can verify the result.

[MemoryDiagnoser]
public class Example
{
    [Benchmark]
    public void Optimized()
    {
        // benchmark code
    }

    [Benchmark]
    public void Default()
    {
        // alternative/default benchmark code
    }
}
```
