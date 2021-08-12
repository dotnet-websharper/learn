# Hello World!

The simplest [sitelet](../server/sitelets/) serves text at the root of the application \(`/`\):

{% tabs %}
{% tab title="Main.fs" %}
```fsharp
module Site

open WebSharper
open WebSharper.Sitelets

[<Website>]
let Main = Application.Text (fun ctx -> "Hello World!")
```
{% endtab %}
{% endtabs %}

[![](http://i.imgur.com/fZgqeKjm.png)](http://i.imgur.com/fZgqeKjl.png)

## Steps to try

1\) Create an empty F\# ASP.NET Core project

```text
dotnet new web -lang f# -n HelloWorld
```

2\) Add the `WebSharper` and `WebSharper.AspNetCore` packages to it:

```text
dotnet add package WebSharper
dotnet add package WebSharper.AspNetCore
```

3\) Add `Main.fs` as shown above to the project as your first code file.

4\) Modify `Startup.fs` as follows:

```fsharp
...
open WebSharper.AspNetCore

type Startup() =

    member this.ConfigureServices(services: IServiceCollection) =
        services.AddSitelet(Site.Main)
            .AddAuthentication("WebSharper")
            .AddCookie("WebSharper", fun options -> ())
        |> ignore

    member this.Configure(app: IApplicationBuilder, env: IWebHostEnvironment) =
        if env.IsDevelopment() then app.UseDeveloperExceptionPage() |> ignore

        app.UseAuthentication()
            .UseStaticFiles()
            .UseWebSharper()
            .Run(fun context ->
                context.Response.StatusCode <- 404
                context.Response.WriteAsync("Page not found"))
```

5\) Run the app with `dotnet run`.

