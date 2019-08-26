# Contributor Guide

## Context as First Argument

Values of the context.Context type carry security credentials, tracing information, 
deadlines, and cancellation signals across API and process boundaries. Go programs 
pass Contexts explicitly along the entire function call chain from incoming RPCs 
and HTTP requests to outgoing requests.

Most functions that use a Context should accept it as their first parameter.


## Declaring Empty Slices

When declaring an empty slice, prefer

```go
var t []string
```

over

```go
t := []string{}
```

The former declares a nil slice value, while the latter is non-nil but zero-length. They are functionally equivalent-their `len` and `cap` are both zero `tbut the nil slice is the preferred style.

Note that there are limited circumstances where a non-nil but zero-length slice is preferred, such as when encoding JSON objects (a `nil` slice encodes to `null`, while `[]string{}` encodes to the JSON array `[]`).

When designing interfaces, avoid making a distinction between a nil slice and a non-nil, zero-length slice, as this can lead to subtle programming errors.

For more discussion about nil in Go see Francesc Campoy's talk [Understanding Nil](https://www.youtube.com/watch?v=ynoY2xz-F8s).


