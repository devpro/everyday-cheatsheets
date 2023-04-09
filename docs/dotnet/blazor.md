# Blazor

> Use the power of .NET and C# to build full stack web apps without writing a line of JavaScript.

→ [dotnet.microsoft.com/apps/aspnet/web-apps/blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor)

## Learn

### Getting started

* [Documentation](https://learn.microsoft.com/en-us/aspnet/core/blazor/)
* [Tutorials](https://learn.microsoft.com/en-us/aspnet/core/blazor/tutorials)
* [Blazor workshop](https://github.com/dotnet-presentations/blazor-workshop)

### Fundamentals

* [Configuration](https://docs.microsoft.com/en-us/aspnet/core/blazor/fundamentals/configuration)
* [Debug](https://docs.microsoft.com/en-us/aspnet/core/blazor/debug)
* [State management](https://docs.microsoft.com/en-us/aspnet/core/blazor/state-management)
* [Security](https://docs.microsoft.com/en-us/aspnet/core/blazor/security/)

### Additional readings

* [Integrating Blazor Components into Existing Asp.Net Core MVC Applications](https://medium.com/@waelkdouh/integrating-blazor-components-into-existing-asp-net-core-mvc-applications-b1a2aec4ac1f) - Jan 7, 2020
* [Blazor Server in .NET Core 3.0 scenarios and performance](https://devblogs.microsoft.com/aspnet/blazor-server-in-net-core-3-0-scenarios-and-performance/) - Oct 10, 2019

### Samples

* [dotnet/blazor-samples](https://github.com/dotnet/blazor-samples)
* [learn.microsoft.com/samples](https://learn.microsoft.com/en-us/samples/browse/?expanded=dotnet&products=blazor)
* [AdrienTorris/awesome-blazor](https://github.com/AdrienTorris/awesome-blazor#sample-projects)
* [davidfowl/TodoApi](https://github.com/davidfowl/TodoApi)
* [iammukeshm/Blazor.Learner](https://github.com/iammukeshm/Blazor.Learner)
* [Naveen512/Blazor-webassembly-authentication-scratch](https://github.com/Naveen512/Blazor-webassembly-authentication-scratch)

## Command line

```bash
# create a new Blazor Server App project
dotnet new blazorserver -o <project-name>

# create a new Blazor WebAssembly App project
dotnet new blazorwasm -o <project-name>

# create a new Razor component
dotnet new razorcomponent -n <component-name> -o <folder>

# create a new Razor page
dotnet new page -n <page-name> -o <folder>
```

## Tips

### Local debug

* [`dotnet watch`](https://github.com/dotnet/AspNetCore.Docs/blob/master/aspnetcore/tutorials/dotnet-watch.md)

## Recipes

### Authentication

* [ASP.NET Core Blazor authentication and authorization](https://docs.microsoft.com/en-us/aspnet/core/blazor/security/)
  * [Secure ASP.NET Core Blazor WebAssembly](https://docs.microsoft.com/en-us/aspnet/core/blazor/security/webassembly/)
* [Blazor Google Auth Sample](https://github.com/javiercn/BlazorGoogleAuthSample)
* [Authentication and Authorization by Steve Sanderson](https://gist.github.com/SteveSandersonMS/175a08dcdccb384a52ba760122cd2eda)
* [StackOverflow #59909081 about page reload](https://stackoverflow.com/questions/59909081/blazor-client-web-assembly-authenticationstate-updates-only-after-page-reloadi)

### Local storage

* [blazored/LocalStorage](https://github.com/blazored/LocalStorage)

## Events

Date | Name | Resources
---- | ---- | ---------
Jun 18, 2020 | BlazorDay 2020 | [Video](https://www.youtube.com/watch?v=XoizucRjxgU&feature=youtu.be)
