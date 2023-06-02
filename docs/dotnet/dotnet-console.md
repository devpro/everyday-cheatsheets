# .NET Console applications

## Learn

### Libraries

- [commandlineparser/commandline](https://github.com/commandlineparser/commandline): "C# command line parser that brings standardized *nix getopt style, for .NET"

### Deployment

- [Deploying .NET Core apps with command-line interface (CLI) tools](https://docs.microsoft.com/en-us/dotnet/core/deploying/deploy-with-cli)

### Examples

- [dotnet/try-convert](https://github.com/dotnet/try-convert): "Sample tool showing how to build a global tool and also help you convert projects to .NET Core"

## Recipes

### Working with processes

- Get the list of active processes

```csharp
var processes = System.Diagnostics.Process.GetProcesses();
```

- Start a new process

```csharp
using System.Diagnostics;
using (var process = new Process()
{
    StartInfo = new ProcessStartInfo
    {
        FileName               = "my\path\file.exe",
        Arguments              = "my arguments",
        RedirectStandardOutput = true,
        UseShellExecute        = false,
        CreateNoWindow         = true,
        Verb                   = "runas"
    }
})
{
    process.Start();
    var result = process.StandardOutput.ReadToEnd();
    process.WaitForExit();
    return result;
}
```
