``` ini

BenchmarkDotNet=v0.11.5, OS=Windows 10.0.18362
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview5-011568
  [Host] : .NET Core 3.0.0-preview5-27626-15 (CoreCLR 4.6.27622.75, CoreFX 4.700.19.22408), 64bit RyuJIT
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.8.3801.0
  Core   : .NET Core 3.0.0-preview5-27626-15 (CoreCLR 4.6.27622.75, CoreFX 4.700.19.22408), 64bit RyuJIT

Jit=RyuJit  Platform=X64  

```
|              Method |  Job | Runtime | InitialSetSize |        Mean |      Error |     StdDev | Ratio | RatioSD | Gen 0 | Gen 1 | Gen 2 | Allocated |
|-------------------- |----- |-------- |--------------- |------------:|-----------:|-----------:|------:|--------:|------:|------:|------:|----------:|
|     **HashSet_Hashset** |  **Clr** |     **Clr** |          **32000** |    **540.0 us** |  **10.787 us** |  **11.542 us** |  **1.00** |    **0.00** |     **-** |     **-** |     **-** |      **48 B** |
| PooledSet_PooledSet |  Clr |     Clr |          32000 |    561.2 us |  10.826 us |  10.633 us |  1.04 |    0.02 |     - |     - |     - |      48 B |
|        HashSet_Enum |  Clr |     Clr |          32000 |    900.8 us |  17.326 us |  17.017 us |  1.66 |    0.05 |     - |     - |     - |      48 B |
|      PooledSet_Enum |  Clr |     Clr |          32000 |    919.7 us |  17.755 us |  17.438 us |  1.70 |    0.05 |     - |     - |     - |      48 B |
|       HashSet_Array |  Clr |     Clr |          32000 |    895.1 us |  12.566 us |  11.754 us |  1.65 |    0.03 |     - |     - |     - |      40 B |
|     PooledSet_Array |  Clr |     Clr |          32000 |    680.7 us |  13.418 us |  14.914 us |  1.26 |    0.05 |     - |     - |     - |         - |
|                     |      |         |                |             |            |            |       |         |       |       |       |           |
|     HashSet_Hashset | Core |    Core |          32000 |    567.4 us |  10.795 us |  11.086 us |  1.00 |    0.00 |     - |     - |     - |      40 B |
| PooledSet_PooledSet | Core |    Core |          32000 |    552.3 us |   9.354 us |   8.750 us |  0.97 |    0.03 |     - |     - |     - |      40 B |
|        HashSet_Enum | Core |    Core |          32000 |    946.9 us |  14.794 us |  13.839 us |  1.67 |    0.04 |     - |     - |     - |      40 B |
|      PooledSet_Enum | Core |    Core |          32000 |    907.0 us |  16.639 us |  15.564 us |  1.60 |    0.04 |     - |     - |     - |      40 B |
|       HashSet_Array | Core |    Core |          32000 |    894.0 us |  16.655 us |  15.579 us |  1.58 |    0.04 |     - |     - |     - |      32 B |
|     PooledSet_Array | Core |    Core |          32000 |    669.7 us |   7.602 us |   7.111 us |  1.18 |    0.03 |     - |     - |     - |         - |
|                     |      |         |                |             |            |            |       |         |       |       |       |           |
|     **HashSet_Hashset** |  **Clr** |     **Clr** |         **320000** |    **800.7 us** |  **15.850 us** |  **15.566 us** |  **1.00** |    **0.00** |     **-** |     **-** |     **-** |      **48 B** |
| PooledSet_PooledSet |  Clr |     Clr |         320000 |    803.7 us |  15.812 us |  15.529 us |  1.00 |    0.03 |     - |     - |     - |      48 B |
|        HashSet_Enum |  Clr |     Clr |         320000 | 12,254.7 us | 200.259 us | 187.322 us | 15.29 |    0.33 |     - |     - |     - |     128 B |
|      PooledSet_Enum |  Clr |     Clr |         320000 |  9,274.2 us | 176.143 us | 180.886 us | 11.59 |    0.30 |     - |     - |     - |     128 B |
|       HashSet_Array |  Clr |     Clr |         320000 |  8,836.3 us | 141.218 us | 110.254 us | 11.02 |    0.25 |     - |     - |     - |     128 B |
|     PooledSet_Array |  Clr |     Clr |         320000 |  7,067.7 us | 120.936 us | 113.124 us |  8.82 |    0.24 |     - |     - |     - |         - |
|                     |      |         |                |             |            |            |       |         |       |       |       |           |
|     HashSet_Hashset | Core |    Core |         320000 |    814.3 us |  13.312 us |  12.452 us |  1.00 |    0.00 |     - |     - |     - |      40 B |
| PooledSet_PooledSet | Core |    Core |         320000 |    839.2 us |   6.158 us |   5.760 us |  1.03 |    0.02 |     - |     - |     - |      40 B |
|        HashSet_Enum | Core |    Core |         320000 |  9,547.3 us | 188.459 us | 176.285 us | 11.73 |    0.23 |     - |     - |     - |      40 B |
|      PooledSet_Enum | Core |    Core |         320000 |  9,245.2 us | 120.679 us | 112.884 us | 11.36 |    0.29 |     - |     - |     - |      40 B |
|       HashSet_Array | Core |    Core |         320000 |  9,022.9 us | 116.004 us | 108.511 us | 11.08 |    0.22 |     - |     - |     - |      32 B |
|     PooledSet_Array | Core |    Core |         320000 |  6,874.2 us |  43.772 us |  40.945 us |  8.44 |    0.14 |     - |     - |     - |         - |