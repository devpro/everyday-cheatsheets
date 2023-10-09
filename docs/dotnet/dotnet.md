# .NET

> .NET is the free, open-source, cross-platform framework for building modern apps and powerful cloud services

→ [dot.net](https://dotnet.microsoft.com/), [docs](https://docs.microsoft.com/en-us/dotnet/), [GitHub](https://github.com/Microsoft)

## Learn

## Quickstart

* [Get started tutorials](https://dotnet.microsoft.com/learn)

### Key components

* [**CoreCLR**](https://github.com/dotnet/coreclr) (Common Language Runtime) is the **runtime** for .NET Core. It includes the garbage collector, JIT compiler, primitive data types and low-level classes.
* [**Roslyn**](https://docs.microsoft.com/en-us/dotnet/csharp/roslyn-sdk/), .NET **compiler**, provides C# and Visual Basic languages with rich code analysis APIs. See [GitHub](https://github.com/dotnet/roslyn).
* [.NET CLI](./dotnet-cli.md)

### Guides

* [.NET Architecture Guides](https://dotnet.microsoft.com/learn/dotnet/architecture-guides)
  * [.NET Microservices Architecture Guidance](https://dotnet.microsoft.com/learn/aspnet/microservices-architecture) ([Microservice architecture with ASP.NET Core](https://channel9.msdn.com/Events/Build/2017/T6051) May 08, 2017, [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers))
* [.NET at Pivotal](https://content.pivotal.io/dotnet)

### Videos

* [Learning videos](https://dotnet.microsoft.com/learn/videos)
* [Youtube channel](https://www.youtube.com/channel/UCvtT19MZW8dq5Wwfu6B0oxw)

## Ecosystem

### .NET Foundation

→ [dotnetfoundation.org](https://dotnetfoundation.org/)

### Open source libraries & tools

* [dotnet/sourcelink](https://github.com/dotnet/sourcelink)
* [spectreconsole/spectre.console](https://github.com/spectreconsole/spectre.console)
* [nuke-build/nuke](https://github.com/nuke-build/nuke)
* [dotnet/format](https://github.com/dotnet/format)

  ```dos
  dotnet tool install -g dotnet-format
  ```

## Recipes

### Password hashing

* [Password Hashing](https://docs.microsoft.com/en-us/aspnet/core/security/data-protection/consumer-apis/password-hashing)
* [Hashing passwords in .NET Core with tips](https://www.codeproject.com/articles/1104467/hashing-passwords-in-net-core-with-tips)
* [Encode and decode a string, with password and salt, in dotnet core](https://stackoverflow.com/questions/42459487/encode-and-decode-a-string-with-password-and-salt-in-dotnet-core)
* [Exploring the ASP.NET Core Identity PasswordHasher](https://andrewlock.net/exploring-the-asp-net-core-identity-passwordhasher/)
* [IPasswordHasher Interface](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.identity.ipasswordhasher-1?view=aspnetcore-2.0)

### Code obfuscation

#### dotfuscator ([overview](https://www.preemptive.com/products/dotfuscator/overview))

`dotfuscator` is a tool, available in Community Edition, that can be installed from `Visual Studio 2017`.

Readings:

* From docs.microsoft.com:
  * [ObfuscateAssemblyAttribute Class](https://docs.microsoft.com/en-us/dotnet/api/system.reflection.obfuscateassemblyattribute?view=netframework-4.7.1)
  * [Dotfuscator Community Edition (CE)](https://docs.microsoft.com/en-us/visualstudio/ide/dotfuscator/)
  * [Install Dotfuscator Community Edition (CE)](https://docs.microsoft.com/en-us/visualstudio/ide/dotfuscator/install)
* From preemptive.com:
  * [Overview](https://www.preemptive.com/products/dotfuscator/overview)
  * [Downloads](https://www.preemptive.com/products/dotfuscator/downloads)
  * [Building in the Cloud with Dotfuscator Community Edition](https://www.preemptive.com/blog/article/905-building-in-the-cloud-with-dotfuscator-community-edition/91-dotfuscator-ce)
  * [Getting started from VS 2017](https://www.preemptive.com/blog/article/904-dotfuscator-in-visual-studio-2017/91-dotfuscator-ce)
  * [Getting Started](https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html)
* From marketplace.visualstudio.com:
  * [Dotfuscator Community Edition Build Task](https://marketplace.visualstudio.com/items?itemName=PreEmptiveSolutions.dotfuscator-ce-vsts)

#### Decompile .NET Code tools

* ILSpy ([icsharpcode/ILSpy](https://github.com/icsharpcode/ILSpy))
* JustDecompile ([telerik.com](https://www.telerik.com/products/decompiler.aspx))

### Package management

* FuGet
  * [Scott Hansleman - NuGet's fancy older sibling FuGet gives you a whole new view of the .NET packaging ecosystem](https://www.hanselman.com/blog/NuGetsFancyOlderSiblingFuGetGivesYouAWholeNewViewOfTheNETPackagingEcosystem.aspx)
* Nukeeper
  * [Scott Hanselman - NuKeeper for automated NuGet Package Reference Updates on Build Servers](https://www.hanselman.com/blog/NuKeeperForAutomatedNuGetPackageReferenceUpdatesOnBuildServers.aspx)
* Dependabot
  * [Scott Hanselman - Dependabot for .NET Core dependency tracking in GitHub](https://www.hanselman.com/blog/DependabotForNETCoreDependencyTrackingInGitHub.aspx)
* SourceLink
  * [Scott Hanselman - Exploring .NET Core's SourceLink - Stepping into the Source Code of NuGet packages you don't own](https://www.hanselman.com/blog/ExploringNETCoresSourceLinkSteppingIntoTheSourceCodeOfNuGetPackagesYouDontOwn.aspx)

### Code analysis

* [.NET API analyzer](https://docs.microsoft.com/en-us/dotnet/standard/analyzers/api-analyzer)
* [Overview of static code analysis for managed code in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/code-quality/code-analysis-for-managed-code-overview?view=vs-2017)
* FxCop
* StyleCop

### Performances

* [BenchmarkDotNet](https://benchmarkdotnet.org) ([GitHub](https://github.com/dotnet/BenchmarkDotNet))

### Local debugging

* Certificate management: [Stackoverflow questions](https://stackoverflow.com/questions/56409580/trouble-trusting-local-https-certificate-in-asp-net-core)

### Others

* [App Metrics](https://www.app-metrics.io/)
* [nuke](http://www.nuke.build/index.html)

## Additional readings

### Blogs

* [meziantou.net](https://www.meziantou.net/)
