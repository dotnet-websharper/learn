# Single-page applications \(SPAs\)

> To get started easily, you can quickly create a sample SPA with `dotnet` as follows:
>
> ```text
> dotnet new websharper-spa -lang f# -n MySPA
> ```

The following creates an SPA that uses an empty HTML document and a header node:

```fsharp
module YourApp

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

[![](http://i.imgur.com/xYITvCqm.png)](http://i.imgur.com/xYITvCql.png)

