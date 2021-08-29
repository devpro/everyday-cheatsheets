# C#

[Documentation](https://docs.microsoft.com/en-us/dotnet/csharp/)

## Versions

- [C# 8.0](/docs/csharp80.md)

## Recipes

### Synchronous call to an asynchronous method

```csharp
// if CallServiceAsync returns Task (void)
var task = Task.Run(() => CallServiceAsync(url, action));
task.Wait();
```
