# RESTvsGRPC
Evaluating Performance of REST vs. gRPC

## dotnet run -p RestAPI.csproj -c Release
Starts the ASP.NET MVC Core REST API

## dotnet run -p GrpcAPI.csproj -c Release
Starts the GRPC Service

## dotnet run -p RESTvsGRPC.csproj -c Release
Runs the benchmark on the above services

# Benchmark for .NET Core 3.0 

``` ini

BenchmarkDotNet=v0.11.5, OS=Windows 10.0.18362
Intel Core i7-7820HQ CPU 2.90GHz (Kaby Lake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100
  [Host]     : .NET Core 3.0.0 (CoreCLR 4.700.19.46205, CoreFX 4.700.19.46214), 64bit RyuJIT
  DefaultJob : .NET Core 3.0.0 (CoreCLR 4.700.19.46205, CoreFX 4.700.19.46214), 64bit RyuJIT


```
| Method                         | IterationCount |         Mean |         Error |        StdDev |
| ------------------------------ | -------------- | -----------: | ------------: | ------------: |
| **RestGetSmallPayloadAsync**   | **100**        | **14.15 ms** | **0.2825 ms** | **0.5706 ms** |
| RestGetLargePayloadAsync       | 100            |  1,279.23 ms |    21.4717 ms |    22.0498 ms |
| RestPostLargePayloadAsync      | 100            |  1,644.70 ms |    20.9949 ms |    19.6386 ms |
| GrpcGetSmallPayloadAsync       | 100            |     18.67 ms |     0.3727 ms |     0.7779 ms |
| GrpcStreamLargePayloadAsync    | 100            |  1,677.17 ms |    30.6976 ms |    39.9155 ms |
| GrpcGetLargePayloadAsListAsync | 100            |    208.17 ms |     4.0576 ms |     7.6211 ms |
| GrpcPostLargePayloadAsync      | 100            |    207.18 ms |     4.0394 ms |    10.7820 ms |
| **RestGetSmallPayloadAsync**   | **200**        | **27.87 ms** | **0.5561 ms** | **1.0308 ms** |
| RestGetLargePayloadAsync       | 200            |  2,579.35 ms |    33.2682 ms |    29.4914 ms |
| RestPostLargePayloadAsync      | 200            |  3,303.59 ms |    37.9533 ms |    33.6446 ms |
| GrpcGetSmallPayloadAsync       | 200            |     37.04 ms |     0.7390 ms |     1.5749 ms |
| GrpcStreamLargePayloadAsync    | 200            |  3,229.51 ms |    62.5833 ms |    52.2599 ms |
| GrpcGetLargePayloadAsListAsync | 200            |    421.68 ms |     8.3405 ms |    16.4633 ms |
| GrpcPostLargePayloadAsync      | 200            |    399.98 ms |     7.9921 ms |    21.3324 ms |

