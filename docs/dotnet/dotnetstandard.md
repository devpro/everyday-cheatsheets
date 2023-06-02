# .NET Standard

> The .NET Standard is a formal specification of .NET APIs that are intended to be available on all .NET implementations.

→ [docs.microsoft.com/dotnet/standard](https://docs.microsoft.com/en-us/dotnet/standard/net-standard)

## Guides

- [Open-source library guidance](https://docs.microsoft.com/en-us/dotnet/standard/library-guidance/)

## Releases

### .NET Standard 2.0

- **.NET Standard is for sharing code**. .NET Standard is a set of APIs that all .NET implementations must provide to conform to the standard. This unifies the .NET implementations and prevents future fragmentation. It replaces Portable Class Libraries (PCLs) as the tool for building .NET libraries that work everywhere.
- **Much bigger API Surface**: We have more than doubled the set of available APIs from 13k in .NET Standard 1.6 to 32k in .NET Standard 2.0. Most of them are existing .NET Framework APIs. These additions make it much easier to port existing code to .NET Standard, and, by extension, to any .NET implementation of .NET Standard, such as .NET Core 2.0 and the upcoming version of UWP.
- **.NET Framework compatibility mode**: The vast majority of NuGet packages are currently still targeting .NET Framework. Many projects are currently blocked from moving to .NET Standard because not all their dependencies are targeting .NET Standard yet. That’s why we added a compatibility mode that allows .NET Standard projects to reference .NET Framework libraries. While this may not work in all cases (for instance, if the .NET Framework binaries use WPF) we found that 70% of all NuGet packages on nuget.org are API compatible with .NET Standard 2.0. So in practice it unblocks many projects.
- **Broad platform support**.

→ [devblogs.microsoft.com/announcing-net-standard-2-0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/)

### .NET Standard 2.1

Highlights:

- `Span<T>`
- Foundational-APIs working with spans
- Reflection emit
- [SIMD](https://en.wikipedia.org/wiki/SIMD)
- `ValueTask` and `ValueTask<T>`
- DbProviderFactories
- General additions

Primary reasons why you may want to update to .NET Standard 2.1:

- Wide support for `Span<T>`
- New language features
  - `IAsyncEnumerable<T>`
  - `Index` and `Range` expressions
  - default interface methods

→ [devblogs.microsoft.com/announcing-net-standard-2-1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/)
