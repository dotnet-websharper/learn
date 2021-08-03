# Updating WebSharper

Once you [install the project templates ](installing-project-templates.md)and create applications based on them, the dependencies of those applications will be pinned to those found in the templates at the time of installation.

You can list the package dependencies in your project with:

```text
> dotnet list package
Project 'SPA01' has the following package references
    [net5.0]:
    Top-level Package            Requested           Resolved
    > FSharp.Core                5.0.0               5.0.0
    > WebSharper                 5.0.0.53-preview1   5.0.0.53-preview1
    > WebSharper.AspNetCore      5.0.0.53-preview1   5.0.0.53-preview1
    > WebSharper.FSharp          5.0.0.53-preview1   5.0.0.53-preview1
    > WebSharper.UI              5.0.0.53-preview1   5.0.0.53-preview1
```

### Checking for the latest WebSharper and other package versions

You can check if an update to a package is available by going directly to:

* The standard NuGet feed for public releases: [https://www.nuget.org/packages?q=websharper](https://www.nuget.org/packages?q=websharper)
* The GitHub package feed for beta releases: [https://github.com/orgs/dotnet-websharper/packages](https://github.com/orgs/dotnet-websharper/packages) 

### Updating a WebSharper package

You can update a given package via `dotnet`, for instance WebSharper itself:

```text
> dotnet add package WebSharper
```



