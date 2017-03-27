# Convert ASCII encoded bytes to int

When working with ASCII encoded bytes you can use this code to convert from byte[] to int without first converting to string and then int.

## Use case

Usefull when your data is stored in byte arrays and you need to convert a value.

## Proof of concept

```
var result = 0;

for (var i = 0; i < count; i++)
{
    result = result * 10 + (bytes[index + i] - '0');
}

return result;
```

## Implementation

```
public static int ConvertToInt(byte[] bytes, int index, int count)
{
    if (index + count >= bytes.length)
        throw  new IndexOutOfRangeException();

    var result = 0;

    for (var i = 0; i < count; i++)
    {
        result = result * 10 + (bytes[index + i] - '0');
    }

    return result;
}
```

## Benchmark

```
    Method |        Mean |    StdErr |    StdDev | Allocated |
---------- |------------ |---------- |---------- |---------- |
 Optimized |   2.6614 ns | 0.0451 ns | 0.2592 ns |       0 B |
   Default | 154.4741 ns | 1.4732 ns | 5.7056 ns |      20 B |
```

```
[MemoryDiagnoser]
public class ConvertBytesToInt
{
    private readonly byte[] _buffer;
    private readonly int _index;
    private readonly int _count;

    public ConvertBytesToInt()
    {
        _buffer = Encoding.UTF8.GetBytes("HTTP/1.1 200 OK\r\nDate: Wed, 06 Jul 2016 18:26:27 GMT\r\nContent-Length: 13\r\nContent-Type");
        _index = 70;
        _count = 2;
    }

    [Benchmark]
    public void Optimized()
    {
        var result = 0;

        for (var i = 0; i < _count; i++)
        {
            result = result * 10 + (_buffer[_index + i] - '0');
        }
    }

    [Benchmark]
    public void Default()
    {
        var result = Convert.ToInt32(Encoding.UTF8.GetString(_buffer, _index, _count));
    }
}
```
