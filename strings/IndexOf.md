# IndexOf

`Needs description.`

## Use case

`Needs documentation on what Ordinal does and why it is faster.`

## Implementation

```
var index = input.IndexOf("Content-Length: ", StringComparison.Ordinal);
```

## Benchmark

```
           Method |          Mean |     StdDev | Allocated |
----------------- |-------------- |----------- |---------- |
          Ordinal |   119.0242 ns |  2.1696 ns |       0 B |
 InvariantCulture |   161.7739 ns |  4.5074 ns |       0 B |
          Default | 2,606.7138 ns | 68.1743 ns |       0 B |
```

```
[MemoryDiagnoser]
public class IndexOf
{
    private const string input = "HTTP/1.1 200 OK\r\nDate: Wed, 06 Jul 2016 18:26:27 GMT\r\nContent-Length: 13\r\nContent-Type";

    [Benchmark]
    public void Ordinal()
    {
        var index = input.IndexOf("Content-Length: ", StringComparison.Ordinal);
    }

    [Benchmark]
    public void InvariantCulture()
    {
        var index = input.IndexOf("Content-Length: ", StringComparison.InvariantCulture);
    }

    [Benchmark]
    public void Default()
    {
        var index = input.IndexOf("Content-Length: ");
    }
}
```
