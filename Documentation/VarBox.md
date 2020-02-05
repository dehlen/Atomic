# VarBox

An arbitrary container which stores a **variable** value of type `T`.

``` swift
public final class VarBox<T>
```

This main purpose of this object is to encapsulate value types so that they can be used like a reference type
(e.g. pass value types around without copying them, "share" value types between closures, etc)

## Initializers

## init(\_:)

Instantiate a new variable value box with the given value.

``` swift
public init(_ value: T)
```

  - parameter value: the value to encapsulate.

### Returns

a newly instantiated box with the encapsulated value.

## Properties

## value

The encapsulated value.

``` swift
var value: T
```
