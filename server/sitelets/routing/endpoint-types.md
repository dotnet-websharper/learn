---
description: Representing HTTP requests in the type system and .NET values as URLs.
---

# Endpoint types

## Basic types

You can use the following basic types in your endpoint type, each are encoded as a single URL path segment:

| Type | URL example \(suffix to webapp\) | Parsed endpoint |
| :--- | :--- | :--- |
| `string` | /asdf | `"asdf"` |
| `float` | /1.2 | `1.2` |
| `int` | /123 | `123` |

## Composite types

You can compose the above basic types \(and the composite types in this section, recursively\) to communicate more structured data. Assuming you have an int and a string pair of values, you can combine them into **tuples** and **records**:

| Type | URL example | Parsed endpoint |
| :--- | :--- | :--- |
| `int * string` | /123/asdf | `(123, "asdf")` |
| `{ Number: int; Name: string }` | /123/asdf | `{ Number=123; Name="asdf" }` |

You can also use **unions**, where the case name is encoded as a path segment, followed by the segments of its arguments:

| Type | URL example | Parsed endpoint |
| :--- | :--- | :--- |
| `string option` | /Some/asdf | `Some "asdf"` |
| `(int * string) option` | /Some/123/asdf | `Some (123, "asdf)` |

Lists and arrays are encoded as a number representing the length, followed by each element:

| Type | URL example | Parsed endpoint |
| :--- | :--- | :--- |
| `string list` | /2/asdf/qwerty | `["asdf"; "querty"]` |
| `(int * string) list` | /2/123/asdf/1/xyz | `[(123, "asdf"); (1, "xyz")]` |

## Enumerations

Enumerations are encoded as their underlying type:

| Type | Url example | Parsed endpoint |
| :--- | :--- | :--- |
| `System.IO.FileAccess` | /3 | `System.IO.FileAccess.ReadWrite` |

## Other types

`DateTime` values are serialized with the format `yyyy-MM-dd-HH.mm.ss`. You can customize this and many other aspects of parsing requests to endpoint values by endpoint modifiers. You can read about them in:

{% page-ref page="endpoint-modifiers.md" %}





