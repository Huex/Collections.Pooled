``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview-009812
  [Host] : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT
  Core   : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT

Job=Core  Runtime=Core  

```
|                    Method |      N |           Mean |         Error |        StdDev | Ratio | RatioSD |  Gen 0/1k Op |  Gen 1/1k Op |  Gen 2/1k Op | Allocated Memory/Op |
|-------------------------- |------- |---------------:|--------------:|--------------:|------:|--------:|-------------:|-------------:|-------------:|--------------------:|
|   **ListAddRangeICollection** |   **1000** |     **2,071.8 us** |      **41.39 us** |     **102.30 us** |  **1.00** |    **0.00** |    **6451.1719** |            **-** |            **-** |         **19843.75 KB** |
| PooledAddRangeICollection |   1000 |       756.5 us |      12.54 us |      11.12 us |  0.35 |    0.02 |      63.4766 |            - |            - |           195.31 KB |
|   ListAddRangeIEnumerable |   1000 |    46,797.0 us |     914.46 us |     810.64 us | 21.78 |    1.24 |   13416.6667 |            - |            - |         41367.19 KB |
| PooledAddRangeIEnumerable |   1000 |    53,108.1 us |     501.09 us |     444.21 us | 24.74 |    1.65 |     100.0000 |            - |            - |           390.63 KB |
|                           |        |                |               |               |       |         |              |              |              |                     |
|   **ListAddRangeICollection** |  **10000** |    **19,688.9 us** |     **391.48 us** |     **715.84 us** |  **1.00** |    **0.00** |   **63281.2500** |            **-** |            **-** |           **195625 KB** |
| PooledAddRangeICollection |  10000 |     7,713.2 us |     145.34 us |     149.26 us |  0.40 |    0.02 |      62.5000 |            - |            - |           195.31 KB |
|   ListAddRangeIEnumerable |  10000 |   458,684.4 us |   9,074.38 us |  12,114.04 us | 23.52 |    1.13 |  208000.0000 |            - |            - |        641835.94 KB |
| PooledAddRangeIEnumerable |  10000 |   494,194.8 us |   9,841.87 us |  12,797.21 us | 25.35 |    1.22 |            - |            - |            - |           390.63 KB |
|                           |        |                |               |               |       |         |              |              |              |                     |
|   **ListAddRangeICollection** | **100000** | **1,189,165.1 us** |  **32,998.25 us** |  **45,168.38 us** |  **1.00** |    **0.00** |  **624000.0000** |  **624000.0000** |  **624000.0000** |        **1953437.5 KB** |
| PooledAddRangeICollection | 100000 |    77,564.3 us |   1,439.57 us |   1,478.34 us |  0.07 |    0.00 |            - |            - |            - |           195.31 KB |
|   ListAddRangeIEnumerable | 100000 | 6,208,284.2 us | 119,681.03 us | 267,683.78 us |  5.34 |    0.30 | 1428000.0000 | 1428000.0000 | 1428000.0000 |        5122187.5 KB |
| PooledAddRangeIEnumerable | 100000 | 4,543,255.2 us |  79,985.60 us |  74,818.58 us |  3.84 |    0.15 |            - |            - |            - |           390.63 KB |