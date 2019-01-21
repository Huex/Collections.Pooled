``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
  [Host] : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3260.0
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3260.0

Job=Clr  Runtime=Clr  

```
|                    Method |      N |         Mean |      Error |     StdDev | Ratio | RatioSD |  Gen 0/1k Op |  Gen 1/1k Op |  Gen 2/1k Op | Allocated Memory/Op |
|-------------------------- |------- |-------------:|-----------:|-----------:|------:|--------:|-------------:|-------------:|-------------:|--------------------:|
|   **ListAddRangeICollection** |   **1000** |     **4.178 ms** |  **0.0516 ms** |  **0.0458 ms** |  **1.00** |    **0.00** |   **12851.5625** |            **-** |            **-** |         **39536.68 KB** |
| PooledAddRangeICollection |   1000 |     5.550 ms |  0.0419 ms |  0.0392 ms |  1.33 |    0.02 |      62.5000 |            - |            - |           195.32 KB |
|   ListAddRangeIEnumerable |   1000 |    52.662 ms |  0.7898 ms |  0.7388 ms | 12.61 |    0.17 |   13400.0000 |            - |            - |         41373.23 KB |
| PooledAddRangeIEnumerable |   1000 |    59.119 ms |  0.2286 ms |  0.2138 ms | 14.15 |    0.17 |     111.1111 |            - |            - |           391.12 KB |
|                           |        |              |            |            |       |         |              |              |              |                     |
|   **ListAddRangeICollection** |  **10000** |    **39.295 ms** |  **0.4281 ms** |  **0.3795 ms** |  **1.00** |    **0.00** |  **126538.4615** |            **-** |            **-** |        **392106.67 KB** |
| PooledAddRangeICollection |  10000 |    76.380 ms |  0.4204 ms |  0.3932 ms |  1.94 |    0.02 |            - |            - |            - |           195.43 KB |
|   ListAddRangeIEnumerable |  10000 |   537.432 ms |  3.3123 ms |  3.0983 ms | 13.68 |    0.16 |  208000.0000 |            - |            - |         642601.5 KB |
| PooledAddRangeIEnumerable |  10000 |   640.023 ms |  3.0679 ms |  2.8697 ms | 16.29 |    0.18 |            - |            - |            - |              392 KB |
|                           |        |              |            |            |       |         |              |              |              |                     |
|   **ListAddRangeICollection** | **100000** | **2,470.396 ms** | **11.7930 ms** | **11.0312 ms** |  **1.00** |    **0.00** | **1249000.0000** | **1249000.0000** | **1249000.0000** |       **3916484.38 KB** |
| PooledAddRangeICollection | 100000 |   639.809 ms |  2.9502 ms |  2.3034 ms |  0.26 |    0.00 |            - |            - |            - |              200 KB |
|   ListAddRangeIEnumerable | 100000 | 6,741.799 ms | 23.9122 ms | 21.1975 ms |  2.73 |    0.02 | 1428000.0000 | 1428000.0000 | 1428000.0000 |       5132721.06 KB |
| PooledAddRangeIEnumerable | 100000 | 6,020.651 ms | 19.8440 ms | 18.5621 ms |  2.44 |    0.01 |            - |            - |            - |              392 KB |