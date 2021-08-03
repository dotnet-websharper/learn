# NuGet packages

WebSharper uses NuGet packages to ship its toolset, proxies to .NET functionality, and bindings to JavaScript libraries. This makes it easy and predictable to add or update various WebSharper components in your applications.

> At the time of writing, WebSharper 5 Preview is **only available** on the WebSharper GitHub feed \(see below\).

WebSharper packages are available on standard NuGet \(1\). If you would like to access the latest developer packages, you can find them on the WebSharper GitHub package feed \(2\):  

```text
> dotnet nuget list source
Registered Sources:
  1.  nuget.org [Enabled]
      https://api.nuget.org/v3/index.json
  2.  dotnet-websharper-GitHub [Enabled]
      https://nuget.pkg.github.com/dotnet-websharper/index.json
```

The standard NuGet feed should come configured on your system when installing the .NET SDK. If you want to configure the WebSharper GitHub feed, you can do so as follows:

```text
ddf
```

### Checking for the latest WebSharper and other versions

You 

### What's in packages

The following core NuGet packages are distributed:

| Package name | What does it provide? |  |
| :--- | :--- | :--- |
| `WebSharper` | the WebSharper Interface Generator \(WIG\) for compiling bindings, the core/standard library proxies |  |
| `WebSharper.FSharp` | The F\#-to-JavaScript compiler \(`WebSharper.Compiler`\), sitelets for remoting and server-side content generation \(`WebSharper.Sitelets`\),  |  |

