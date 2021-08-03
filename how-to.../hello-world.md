# Hello World!

The simplest sitelet serves text on a single endpoint at the root of the application:

```fsharp
module YourApp

open WebSharper
open WebSharper.Sitelets

[<Website>]
let Main = Application.Text (fun ctx -> "Hello World!")
```

[![](http://i.imgur.com/fZgqeKjm.png)](http://i.imgur.com/fZgqeKjl.png)

