``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview-009812
  [Host] : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT
  Core   : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT

Job=Core  Runtime=Core  

```
|                         Method | InitialSetSize |        Mean |      Error |     StdDev | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|------------------------------- |--------------- |------------:|-----------:|-----------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|     **HashSet_IsSuperset_Hashset** |          **32000** |    **599.3 us** |   **8.286 us** |   **7.346 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                **40 B** |
| PooledSet_IsSuperset_PooledSet |          32000 |    599.0 us |   2.711 us |   2.536 us |  1.00 |    0.01 |           - |           - |           - |                40 B |
|        HashSet_IsSuperset_Enum |          32000 |  1,004.9 us |  11.407 us |  10.671 us |  1.68 |    0.03 |           - |           - |           - |                40 B |
|      PooledSet_IsSuperset_Enum |          32000 |    994.1 us |   6.122 us |   5.727 us |  1.66 |    0.02 |           - |           - |           - |                40 B |
|       HashSet_IsSuperset_Array |          32000 |    966.4 us |   7.107 us |   6.300 us |  1.61 |    0.02 |           - |           - |           - |                32 B |
|     PooledSet_IsSuperset_Array |          32000 |    713.7 us |   5.260 us |   4.920 us |  1.19 |    0.01 |           - |           - |           - |                   - |
|                                |                |             |            |            |       |         |             |             |             |                     |
|     **HashSet_IsSuperset_Hashset** |         **320000** |    **904.9 us** |   **2.826 us** |   **2.644 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                **40 B** |
| PooledSet_IsSuperset_PooledSet |         320000 |    891.3 us |   5.738 us |   5.367 us |  0.99 |    0.01 |           - |           - |           - |                40 B |
|        HashSet_IsSuperset_Enum |         320000 | 10,483.4 us |  87.311 us |  81.671 us | 11.59 |    0.10 |           - |           - |           - |                40 B |
|      PooledSet_IsSuperset_Enum |         320000 | 10,224.8 us | 134.574 us | 125.880 us | 11.30 |    0.15 |           - |           - |           - |                40 B |
|       HashSet_IsSuperset_Array |         320000 | 10,212.0 us | 123.408 us | 115.436 us | 11.29 |    0.12 |           - |           - |           - |                32 B |
|     PooledSet_IsSuperset_Array |         320000 |  7,405.8 us | 117.408 us | 104.079 us |  8.18 |    0.12 |           - |           - |           - |                   - |