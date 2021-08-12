---
description: >-
  Implement type-safe micro and REST services, and client-server web
  applications.
---

# Sitelets

Sitelets deal with the server-side: conceptually, they describe how to map incoming HTTP requests to content. They do so by first defining what endpoints the application responds to by using a **type** \(we usually use`EndPoint`\), then mapping **each possible value** of that type to actual content.

{% hint style="info" %}
You can compare sitelets with other F\# web framework notation below: 
{% endhint %}

{% tabs %}
{% tab title="Sitelets" %}
```fsharp
type EndPoint =
    | [<EndPoint "/">] Home
    | [<EndPoint "/api">] of BookApi

and BookApi =
    | [<EndPoint "GET /book">] of GetBook of id:int
    | [<EndPoint "POST /book"; Json "data">] of PostBook of data:BookData
    
and BookData =
    {
        Title: string
        Author: string
        Price: float
    }

let Main =
    Sitelet.Infer (fun ctx -> function
        | Home ->
            ...
        | BookApi (GetBook index) ->
            ...
        | BookApi (PostBook data) ->
            ...
    )
```
{% endtab %}

{% tab title="Giraffe" %}

{% endtab %}

{% tab title="Saturn" %}
```fsharp

```
{% endtab %}
{% endtabs %}

## A closer look

A sitelet internally is a combination of two parts: a **router** and a **controller**, not much unlike in the Model-View-Controller \(MVC\) approach, except with important differences detailed below.

The router maps HTTP requests to values of an endpoint type, but unlike in MVC, it also is responsible for providing a \(mostly\) reverse mapping, i.e. from endpoint values to URLs. Because this latter mapping is for URLs only, the value it produces is only applicable in GET scenarios.

{% hint style="info" %}
You can benefit from the endpoint-to-URL mapping when you need URLs to your pages, and instead of hardwiring them as usual, you can use `ctx.Link`, a function available from the server-side context to give you the precise URL for an endpoint. The value of this becomes more and more obvious as you compose sitelets into larger ones, or need to reshuffle your URL space as your site/application grows.

In the example below we change all the URLs of an API sitelet, with potentially a large number of cross-links between its pages, and all page references will update automatically.

```fsharp
// Move all sitelet URLs under /api
let api =
    Sitelet.Infer (fun ctx -> ...)     // your API sitelet
    |> Seq.singleton
    |> Sitelet.Folder "/api"
```
{% endhint %}

The controller maps endpoint values to HTTP responses, such as a JSON or HTML document, or an error code, preceeded by the applicable content type declaration, if any.

The easiest, and most often used way of creating a sitelet is by "inferring it" \(`Sitelet.Infer`\) from an endpoint to response mapping, as you saw in a single-case scenario above, or a multi-page one below:

```fsharp
module Site

type EndPoint =
    | [<EndPoint "/">] Home
    | [<EndPoint "/echo">] Echo of string
    
let Main =
    Sitelet.Infer (fun ctx -> function
        | Home ->
            Content.Text "Hello world!"
        | Echo msg ->
            Content.Page(
                [
                    h1 [] [text msg]
                [
            )
```

## Routing

While a router is typically associated with a sitelet, it can also be constructed on-demand, typically when a sitelet is not available, such as on the client where an endpoint-based routing is required or in server-side scenarios that don't use sitelets, such as when interoperating with other web servers \(Giraffe, Saturn, etc.\). Consider the following code on the client:

```text
...
```

For a detailed 

You can read more about server-side interoperability in:

{% page-ref page="../asp.net-core-integration.md" %}



## Benefits

Sitelets are always instantiated over/with a given endpoint type `'T`, and this gives some strong guarantees that other, non-typed approaches lack:

1. Map incoming HTTP requests to values of your endpoint type
2. Map the values of your endpoint type to actual content to be served



## EndPoint types

You can read more about what types translate how in endpoints in:

{% page-ref page="routing/endpoint-types.md" %}

## Offline sitelets

You can "print" a sitelet to one or more HTML files, essentially generating its content statically. You can read about offline sitelets in:

{% page-ref page="offline-sitelets.md" %}

## Sitelets API

Next to `Sitelet.Infer`, which infers a URL space from your endpoint type, you can read about and see examples for the other sitelet functions available in:

{% page-ref page="api-sitelets.md" %}

## Responses

You saw how to use `Content.Text` in the USD-HUF conversion service above. You can read about returning other types of content from the server in:

{% page-ref page="responses.md" %}



## Logging

## Accessing the serving context

