# .NET CLI cheatsheet

## Quick Links

* [Get started](https://www.microsoft.com/net/learn/get-started/windows)
* [Documentation](https://docs.microsoft.com/en-us/dotnet/core/)

## Use cases

### Console project

By default .NET Core Console applications reference very few elements.

These are good references to start with (names are self-explanatory!):

* `Microsoft.Extensions.DependencyInjection`
* `Microsoft.Extensions.Logging`
  * `Microsoft.Extensions.Logging.Console`
  * `Microsoft.Extensions.Logging.Debug`
* `Microsoft.Extensions.Configuration`
  * `Microsoft.Extensions.Configuration.Json`

### Json serialization

- [JavaScriptSerializer Class](https://msdn.microsoft.com/en-us/library/system.web.script.serialization.javascriptserializer.aspx)

- Json.NET

You can convert a Json to Xml:

```csharp
// object is needed as the value is an array
var expected = JsonConvert.DeserializeXmlNode($"{{\"object\": {step.ExpectedResponseJsonString}}}", "root");
```
