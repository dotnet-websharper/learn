# Installing project templates

> At the time of writing, WebSharper 5 Preview is **only available** on the WebSharper GitHub feed. Be sure to [have this feed configured](nuget-packages.md) if you want to install WebSharper 5 project templates, otherwise you will fall back to the latest WebSharper 4 templates.

You can install the latest WebSharper project templates via the `dotnet` CLI:

```text
> dotnet new -i WebSharper.Templates
```

> WebSharper templates are shipped as a NuGet package. If you need to install a particular version, you can add the version as a suffix, for instance `::5.0.0.53`.

Various WebSharper project templates are available for F\# and C\#. You can set the default language of your preference in your shell with:

```text
> set DOTNET_NEW_PREFERRED_LANG=F#
```

After installing them, you can list the available project templates on your system:

```text
> dotnet new
...
WebSharper 5 Extension                            websharper-ext           [F#]              WebSharper
WebSharper 5 Library                              websharper-lib           [F#], C#          WebSharper
WebSharper 5 Proxy                                websharper-prx           [F#], C#          WebSharper
WebSharper 5 Client-Server Application            websharper-web           [F#], C#          WebSharper/Web
WebSharper 5 Html Site                            websharper-html          [F#], C#          WebSharper/Web
WebSharper 5 Single Page Application              websharper-spa           [F#], C#          WebSharper/Web
...
```



