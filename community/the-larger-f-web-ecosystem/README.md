# The larger F\# web ecosystem

## Full-stack options

### SAFE Stack vs WebSharper

The [SAFE Stack](https://safe-stack.github.io/) combines [Saturn](https://saturnframework.org/), [Fable](https://fable.io) and [Elmish](https://elmish.github.io/elmish/) as a .NET project template to make it easier to get started with Model-View-Update \(MVU\) applications. Its server-side can be switched to [Giraffe](https://giraffe.wiki/) as well.

WebSharper combines its sitelet representation, a pluggable HTML/DOM abstraction \(for reactive UIs with WebSharper.UI, and ordinary UIs with WebSharper.Html\), and enables multiple styles of applications.

## Client-side options

### Fable vs WebSharper.Compiler

Both tools translate F\# to JavaScript. [Fable](https://fable.io) treats all F\# code client-side, uses modular output, function-level imports and aims to output code that resembles hand-written code to make interacting with JavaScript code easier. WebSharper uses attributes to decide what part of your F\# code is client-side and what is server-side, generates whole-file output.

An integral part of both tools is their ability to bind external JavaScript libraries and make them available for F\# use. For Fable, this is accomplished by translating TypeScript declaration files to F\# source files using [ts2fable](https://github.com/fable-compiler/ts2fable) to be included in the compilation of the consuming code, and by directly binding JavaScript using a combination of F\# interfaces, attributes and helper functions which are then used to drive the JavaScript output.

WebSharper works by ...  

## Server-side options

.

## Benchmarks

You can see various performance aspects of using WebSharper in:

{% page-ref page="benchmarks.md" %}



 

