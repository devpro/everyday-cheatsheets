# C# 7.0

## New features

- [What's new in C# 7.1 and 7.2](https://channel9.msdn.com/Events/Connect/2017/T122)

## Tips

- Async static main methods (for more details look at the discussion on [StackOverflow](https://stackoverflow.com/questions/38114553/are-async-console-applications-supported-in-net-core))

```csharp
using System.Threading.Tasks;

public static async Task Main(string[] args)
{
   await BuildWebHost(args).RunAsync();
}
```
