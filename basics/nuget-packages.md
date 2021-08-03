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
> dotnet nuget add source https://nuget.pkg.github.com/dotnet-websharper/index.json --name dotnet-websharper-GitHub --username <GH_USER> --password <PAT>
```

where `GH_USER` is your GitHub username, and `PAT` is your Personal Access Token \(PAT\) for your GitHub account.

> At the time of writing, GitHub requires authentication to access packages on its Packages feed. To set your access up, create a new PAT at [https://github.com/settings/tokens/new](https://github.com/settings/tokens/new) with the `read:packages` scope, noting the expiration you configure.

### What's in packages

The following core NuGet packages are distributed:

| Package name | What does it provide? |  |
| :--- | :--- | :--- |
| `WebSharper` | the WebSharper Interface Generator \(WIG\) for compiling bindings, the core/standard library proxies |  |
| `WebSharper.FSharp` | The F\#-to-JavaScript compiler \(`WebSharper.Compiler`\), sitelets for remoting and server-side content generation \(`WebSharper.Sitelets`\),  |  |

