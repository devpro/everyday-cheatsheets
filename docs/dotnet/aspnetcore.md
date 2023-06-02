# ASP.NET Core

> ASP.NET Core is the open-source version of ASP.NET, that runs on Windows, Linux, macOS, and Docker.

→ [docs](https://learn.microsoft.com/en-us/aspnet/core/), [code](https://github.com/dotnet/aspnetcore)

## Learn

### Fundamentals

* [Application startup](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/startup)
* [Configuration](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/)
* [Dependency Injection](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection)
* [Error handling](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/error-handling)
* [Host and deploy](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/)
  * [Kestrel web server in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel)
  * [Host ASP.NET Core on Windows with IIS](https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/iis/)
* [Filters](https://docs.microsoft.com/en-us/aspnet/core/mvc/controllers/filters)
* [Filters](https://docs.microsoft.com/en-us/aspnet/core/mvc/controllers/filters)
  * [Dependency Injection in Action Filters](https://www.devtrends.co.uk/blog/dependency-injection-in-action-filters-in-asp.net-core)
* [Identity](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/identity)
* [Integration tests](https://docs.microsoft.com/en-us/aspnet/core/test/integration-tests)
* [Logging](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/logging/)
* [Multiple environments](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/environments)
* [Routing](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/routing)
* [Web server implementations](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/servers/)

### Deep dive

* [Performance Best Practices](https://docs.microsoft.com/en-us/aspnet/core/performance/performance-best-practices)
  * [Performance and reliability](https://docs.microsoft.com/en-us/aspnet/core/performance/performance-best-practices?view=aspnetcore-3.0#performance-and-reliability)
* [The shared framework](https://natemcmaster.com/blog/2018/08/29/netcore-primitives-2/)

## Recipes

### Swagger

* [Get started with Swashbuckle and ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/tutorials/getting-started-with-swashbuckle)

### Logging

* [ASP.NET Core Logging with Azure App Service and Serilog](https://devblogs.microsoft.com/aspnet/asp-net-core-logging/)

### Dispose

* [Four ways to dispose IDisposables in ASP.NET Core](https://andrewlock.net/four-ways-to-dispose-idisposables-in-asp-net-core/)

### Performance

* [ASP.NET Core: Saturating 10GbE at 7+ million request/s](https://www.ageofascent.com/2019/02/04/asp-net-core-saturating-10gbe-at-7-million-requests-per-second/)
* [TechEmpower - Web Framework Benchmarks](https://www.techempower.com/benchmarks/)

### OData

* [Channel 9 - Supercharging your Web APIs with OData and ASP.NET Core](https://channel9.msdn.com/Shows/On-NET/Supercharging-your-Web-APIs-with-OData-and-ASPNET-Core)

### Securing

* [Securing ASP.NET Core 2.0 Applications with JWTs](https://auth0.com/blog/securing-asp-dot-net-core-2-applications-with-jwts/)

### Testing

* [Integration tests in ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/test/integration-tests)
* [Real Browser Integration Testing with Selenium Standalone, Chrome, and ASP.NET Core 2.1](https://www.hanselman.com/blog/RealBrowserIntegrationTestingWithSeleniumStandaloneChromeAndASPNETCore21.aspx) - 2018-05-23
* [IntegrationTestsSample](https://github.com/aspnet/AspNetCore.Docs/tree/master/aspnetcore/test/integration-tests/samples/2.x/IntegrationTestsSample)

### Versioning

* [aspnet-api-versioning](https://github.com/Microsoft/aspnet-api-versioning)
* [Blog of Pi](https://www.blogofpi.com/versioning-web-api/)

### Health checks

* [Xabaril/AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks)

### Packaging

#### WebPack

Articles to review:

* [A complete containerized .NET Core Application microservice that is as small as possible](https://www.ryansouthgate.com/2017/08/29/asp-net-core-and-webpack-part-1/)
* [Setting up Webpack in ASP.NET Core](https://cecilphillip.com/setting-up-webpack-in-asp-net-core/)
* [ReactJs Webpack and ASP.NET Core](https://sensibledev.com/reactjs-webpack-and-asp-net-core/#postSummary)
* [How to use Webpack in ASP.Net core projects; a basic React Template sample](https://codeburst.io/how-to-use-webpack-in-asp-net-core-projects-a-basic-react-template-sample-25a3681a5fc2)
* [BUNDLING IN .NET CORE MVC APPLICATIONS WITH WEBPACK](https://dotnetcore.gaprogman.com/2017/01/05/bundling-in-net-core-mvc-applications-with-webpack/)
* [How to include Bootstrap in your project with Webpack](https://stevenwestmoreland.com/2018/01/how-to-include-bootstrap-in-your-project-with-webpack.html)

### Controller action status code

```csharp
public IActionResult Post([FromBody]string action)
{
    if (...)
    {
        return StatusCode(423);
    }

    return Ok(new ... {});
  }
}
```

### Authentication

#### Use Azure Directory

* Go to Azure Portal and create an application in Azure Active Directory: [Integrating Azure AD into an ASP.NET Core web app](https://azure.microsoft.com/en-us/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

* Examples: [GitHub Azure-Samples/active-directory-dotnet-webapp-openidconnect-aspnetcore](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect-aspnetcore) or run `dotnet new mvc -o dotnetadauth --auth SingleOrg --client-id <clientId> --tenant-id <tenantId> --domain <domainName>`

* Edit csproj file

```xml
<PackageReference Include="Microsoft.AspNetCore.Authentication.AzureAD.UI" Version="2.1.1" />
```

* Edit `appsettings.json` file

```json
"AzureAd": {
  "Instance": "https://login.microsoftonline.com/",
  "Domain": "<domainName>",
  "TenantId": "<tenantId>",
  "ClientId": "<clientId>",
  "CallbackPath": "/signin-oidc"
},
```

* Edit `Startup.cs`:

```csharp
// in ConfigureServices()

services.Configure<CookiePolicyOptions>(options =>
{
    // This lambda determines whether user consent for non-essential cookies is needed for a given request.
    options.CheckConsentNeeded = context => true;
    options.MinimumSameSitePolicy = SameSiteMode.None;
});

services.AddAuthentication(AzureADDefaults.AuthenticationScheme)
    .AddAzureAD(options => Configuration.Bind("AzureAd", options));

services
    .AddMvc(options =>
    {
        var policy = new AuthorizationPolicyBuilder()
            .RequireAuthenticatedUser()
            .Build();
        options.Filters.Add(new AuthorizeFilter(policy));
    })
    .SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

// in Configure()

if (env.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
}
else
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseSpaStaticFiles();
app.UseCookiePolicy();

app.UseAuthentication();
```
