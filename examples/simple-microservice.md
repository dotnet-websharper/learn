---
description: Converting USD to HUF as a microservice.
---

# Simple microservice

Say, you wanted to build a small, singleton web service that converts American dollars \(USD\) to Hungarian forints \(HUF\). You would like to pass the USD amount and get back the equivalent HUF figure. You can implement that as follows \(you can use a `websharper-min` template and replace `Main.fs` with the content below\):

{% tabs %}
{% tab title="Main.fs" %}
```fsharp
module Site

open WebSharper.Sitelets

type EndPoint = float

module Server =
    let LookupUsdHufRate () = 300.0     // Put your logic here

let Main =
    Sitelet.Infer (fun ctx -> function
        | usd ->
            let rate = Server.LookupUsdHufRate()
            Content.Text (string (rate*usd))
    )

```
{% endtab %}
{% endtabs %}

Here, `Site.Main` is a `Sitelet<float>`, responding to float values with the corresponding HUF figure. Booting up this service, you can quickly test it:

{% api-method method="get" host="http://localhost:5000" path="/125" %}
{% api-method-summary %}
Convert 125 USD to HUF
{% endapi-method-summary %}

{% api-method-description %}
Convert USD to HUF
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="USD" type="number" required=true %}
USD amount
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Return the HUF equivalent
{% endapi-method-response-example-description %}

```
37500
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## 

