``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
  [Host] : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3260.0
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3260.0

Job=Clr  Runtime=Clr  

```
|                       Method |      N |   Type |           Mean |         Error |        StdDev | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|----------------------------- |------- |------- |---------------:|--------------:|--------------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|   **ListICollectionConstructor** |   **1000** |    **Int** |       **392.1 us** |      **6.457 us** |      **6.040 us** |  **1.00** |    **0.00** |   **1290.0391** |           **-** |           **-** |          **3968.97 KB** |
| PooledICollectionConstructor |   1000 |    Int |     1,141.6 us |      7.274 us |      6.448 us |  2.91 |    0.05 |     11.7188 |           - |           - |            39.06 KB |
|   ListIEnumerableConstructor |   1000 |    Int |    10,104.1 us |    102.008 us |     95.418 us | 25.77 |    0.50 |   2687.5000 |           - |           - |          8274.68 KB |
| PooledIEnumerableConstructor |   1000 |    Int |     9,121.7 us |     35.617 us |     29.742 us | 23.27 |    0.27 |     15.6250 |           - |           - |            78.13 KB |
|                              |        |        |                |               |               |       |         |             |             |             |                     |
|   **ListICollectionConstructor** |   **1000** | **String** |     **1,059.4 us** |      **8.986 us** |      **8.405 us** |  **1.00** |    **0.00** |   **2556.6406** |           **-** |           **-** |          **7876.89 KB** |
| PooledICollectionConstructor |   1000 | String |     3,016.0 us |     32.199 us |     30.119 us |  2.85 |    0.04 |     11.7188 |           - |           - |            39.06 KB |
|   ListIEnumerableConstructor |   1000 | String |    14,748.8 us |    101.641 us |     95.075 us | 13.92 |    0.11 |   5281.2500 |           - |           - |         16271.19 KB |
| PooledIEnumerableConstructor |   1000 | String |    16,645.6 us |     82.942 us |     77.584 us | 15.71 |    0.16 |           - |           - |           - |               86 KB |
|                              |        |        |                |               |               |       |         |             |             |             |                     |
|   **ListICollectionConstructor** |  **10000** |    **Int** |     **3,610.5 us** |     **38.585 us** |     **34.205 us** |  **1.00** |    **0.00** |  **12656.2500** |           **-** |           **-** |         **39210.69 KB** |
| PooledICollectionConstructor |  10000 |    Int |    15,242.8 us |     53.593 us |     47.509 us |  4.22 |    0.03 |           - |           - |           - |            39.13 KB |
|   ListIEnumerableConstructor |  10000 |    Int |    97,403.0 us |    887.589 us |    830.252 us | 26.98 |    0.39 |  41500.0000 |           - |           - |        128520.83 KB |
| PooledIEnumerableConstructor |  10000 |    Int |    90,991.9 us |    837.272 us |    783.185 us | 25.21 |    0.34 |           - |           - |           - |            78.67 KB |
|                              |        |        |                |               |               |       |         |             |             |             |                     |
|   **ListICollectionConstructor** |  **10000** | **String** |     **9,473.5 us** |     **71.045 us** |     **66.455 us** |  **1.00** |    **0.00** |  **24984.3750** |           **-** |           **-** |         **78371.88 KB** |
| PooledICollectionConstructor |  10000 | String |    39,450.4 us |    212.160 us |    188.075 us |  4.16 |    0.04 |           - |           - |           - |            39.38 KB |
|   ListIEnumerableConstructor |  10000 | String |   210,277.9 us |  2,529.639 us |  2,366.226 us | 22.20 |    0.33 |  41333.3333 |  41333.3333 |  41333.3333 |        256378.94 KB |
| PooledIEnumerableConstructor |  10000 | String |   183,340.8 us |  1,541.530 us |  1,441.949 us | 19.35 |    0.24 |           - |           - |           - |               88 KB |
|                              |        |        |                |               |               |       |         |             |             |             |                     |
|   **ListICollectionConstructor** | **100000** |    **Int** |    **69,652.1 us** |  **1,294.527 us** |  **1,271.399 us** |  **1.00** |    **0.00** |  **23125.0000** |  **23125.0000** |  **23125.0000** |        **390885.92 KB** |
| PooledICollectionConstructor | 100000 |    Int |   132,882.2 us |    855.146 us |    714.086 us |  1.90 |    0.04 |           - |           - |           - |               40 KB |
|   ListIEnumerableConstructor | 100000 |    Int | 1,148,402.0 us | 23,434.389 us | 32,077.256 us | 16.53 |    0.52 | 207000.0000 | 167000.0000 | 165000.0000 |       1027256.91 KB |
| PooledIEnumerableConstructor | 100000 |    Int |   841,692.4 us | 16,652.876 us | 15,577.111 us | 12.09 |    0.34 |           - |           - |           - |               80 KB |
|                              |        |        |                |               |               |       |         |             |             |             |                     |
|   **ListICollectionConstructor** | **100000** | **String** |   **515,205.3 us** |  **9,520.150 us** |  **8,905.154 us** |  **1.00** |    **0.00** |  **31000.0000** |  **31000.0000** |  **31000.0000** |        **781574.23 KB** |
| PooledICollectionConstructor | 100000 | String |   335,606.5 us |  3,795.786 us |  3,550.581 us |  0.65 |    0.02 |           - |           - |           - |               40 KB |
|   ListIEnumerableConstructor | 100000 | String | 1,818,274.9 us |  4,829.271 us |  4,032.660 us |  3.51 |    0.02 | 326000.0000 | 286000.0000 | 283000.0000 |        2053324.8 KB |
| PooledIEnumerableConstructor | 100000 | String | 1,686,428.6 us |  8,040.717 us |  7,521.291 us |  3.27 |    0.06 |           - |           - |           - |               88 KB |