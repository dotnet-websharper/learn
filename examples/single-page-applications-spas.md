# Single-page applications \(SPAs\)

> To get started easily, you can quickly create a sample SPA with `dotnet` as follows:
>
> ```text
> dotnet new websharper-spa -lang f# -n MySPA
> ```

The following creates a [sitelet](../server/sitelets/) for an SPA that uses an empty HTML document and a header node:

{% tabs %}
{% tab title="Main.fs" %}
```fsharp
module Site

open WebSharper
open WebSharper.Sitelets
open WebSharper.UI.Html
open WebSharper.UI.Server

[<Website>]
let Main =
    Application.SinglePage (fun ctx ->
        Content.Page(
            h1 [] [text "Hello World!"]
        )
    )
```
{% endtab %}
{% endtabs %}

[![](http://i.imgur.com/xYITvCqm.png)](http://i.imgur.com/xYITvCql.png)

## Steps to try

1\) Create a new WebSharper server project as shown in the [Hello World! example](hello-world.md).

2\) Replace `Main.fs` with the file above.

3\) Run the app with `dotnet run` .

