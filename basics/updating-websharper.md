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

You can check if an update is available:

```text
> dotnet ..
```

And you can update each dependency via `dotnet`:

```text
> dotnet add reference  
```



