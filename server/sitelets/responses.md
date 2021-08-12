# Responses

You can construct a variety of server responses by describing their HTTP status, headers and body content. Such responses are always asynchronous: all the constructors and combinators described below take and return values of type `Async<Content<'EndPoint>>`.

## Content.Text

You can create plain text responses with `Content.Text`:

```fsharp
Content.Text "Hello world!"
```

## Content.Page

You can create full HTML page responses, with [managed dependencies](../../features.md#dependency-handling) using `Content.Page`:

```fsharp
open WebSharper.UI.Html

Content.Page(
    Title = "Welcome!",
    Head = [
        link [attr.href "/css/style.css"; attr.rel "stylesheet"] []
    ],
    Body = [
        h1 [] [text "Hello world!"] 
    ],
    Doctype = "<!DOCTYPE html>"
)
```

The optional named arguments `Title`, `Head`, `Body` and `Doctype` set the corresponding elements of the HTML page. In its most basic form, you can just supply the body content with another overload:

```fsharp
Content.Page(
    [
        h1 [] [text "Hello world!"]
    ]
)
```

{% hint style="info" %}
Both of the above variants of `Content.Page` construct "managed" HTML documents: prepared to contain and light up client-side WebSharper content. As such, the resulting HTML will contain the following extra content \(in the `head` section\):

1. A `<meta>` tag that contains type information about RPC methods, if empty, it looks like:  `<meta id='websharper-data' content='{"$TYPES":[],"$DATA":{"$V":{}}}' />`  
2. Any script includes that are needed to run the page, depending on its dynamic client-side content. At a bare minimum, this consists of the basic WebSharper runtime script:  `<script src="/Scripts/WebSharper/WebSharper.Core.JavaScript/Runtime.min.js" type="text/javascript" charset="UTF-8">` 
3. A small initialization script block:  `<script type="text/javascript">   if (typeof IntelliFactory !=='undefined') {     IntelliFactory.Runtime.ScriptBasePath = '/Scripts/WebSharper/';     IntelliFactory.Runtime.Start();   } </script>`
{% endhint %}

If you need to return plain-old HTML documents without that extra management, you can use the `Content.Page` overload that takes a single `Doc` value instead:

{% tabs %}
{% tab title="F\#" %}
```fsharp
Content.Page(h1 [] [text "Hello world!"])
```
{% endtab %}

{% tab title="Result" %}
```
<!DOCTYPE html>
<h1>Hello world!</h1>
```
{% endtab %}
{% endtabs %}

You can learn more about constructing server-side HTML:

{% page-ref page="../html.md" %}

## Content.Json

You can easily generate JSON for your data by passing them to [`Content.Json`](https://developers.websharper.com/api/v4.1/WebSharper.Sitelets.Content#Json%60%601). The format is the same as when parsing requests. See here for more information about the JSON format.

