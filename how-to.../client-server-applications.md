# Client-server applications

Multi-page applications have multiple endpoints: pairs of HTTP verbs and paths, and are represented as an annotated **union type** we typically call `Endpoints`. The endpoints, as defined by this union type - given the various annotations on each union case - are mapped to content to be served using `Application.MultiPage`. Links to endpoints in your site can be calculated from the serving context, so you will never have invalid URLs.

{% tabs %}
{% tab title="Main.fs" %}
```fsharp
module Site

open WebSharper
open WebSharper.Sitelets
open WebSharper.UI
open WebSharper.UI.Html
open WebSharper.UI.Server

type Endpoints =
    | [<EndPoint "GET /">] Home
    | [<EndPoint "GET /about">] About

[<Website>]
let Main =
    Application.MultiPage (fun ctx endpoint ->
        let (=>) label endpoint = a [attr.href (ctx.Link endpoint)] [text label]
        match endpoint with
        | Endpoints.Home ->
            Content.Page(
                Body = [
                    h1 [] [text "Hello world!"]
                    "About" => Endpoints.About
                ]
            )
        | Endpoints.About ->
            Content.Page(
                Body = [
                    p [] [text "This is a simple app"]
                    "Home" => Endpoints.Home
                ]
            )
    )
```
{% endtab %}
{% endtabs %}

[![](http://i.imgur.com/WMnmzIPm.png)](http://i.imgur.com/WMnmzIPl.png)

