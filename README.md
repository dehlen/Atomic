# Atomic
<img src="https://img.shields.io/badge/supports-Swift%20Package%20Manager-green.svg">

This package implements an Atomic class that uses [os_unfair_lock](https://developer.apple.com/documentation/os/1646466-os_unfair_lock_lock) (iOS) or [pthread_mutex_t](https://pubs.opengroup.org/onlinepubs/007908799/xsh/pthread_mutex_lock.html) (macOS) to provide synchronized access to a variable.

The implementation was extracted from [ReactiveSwift](https://github.com/ReactiveCocoa/ReactiveSwift/blob/master/Sources/Atomic.swift).


## Installation

Currently only Swift Package Manager is supported. 
Swift Package Manager is a dependency manager built into Xcode.

If you are using Xcode 11 or higher, go to File / Swift Packages / Add Package Dependency... and enter package repository URL https://github.com/dehlen/Atomic.git, then follow the instructions.

To remove the dependency, select the project and open Swift Packages (which is next to Build Settings). You can add and remove packages from this tab.

## Documentation
The documentation is generated thanks to [swift-doc](https://github.com/SwiftDocOrg/swift-doc).
You can find the latest version here: [Documentation](./Documentation).

## Usage
```swift
/// Initialize the variable with the given initial value.
private var myVariable: Atomic<Bool> = Atomic(false)

/// Atomically get, set or modify the value of the variable.
print(myVariable.value)
myVariable.value = true

/// Atomically modifies the variable.
///
/// - parameters:
///   - action: A closure that takes the current value.
///
/// - returns: The result of the action.
myVariable.modify { oldValue in 
    if oldValue {
        return false
    } else {
        return true
    }
}

/// Atomically perform an arbitrary action using the current value of the
/// variable.
///
/// - parameters:
///   - action: A closure that takes the current value.
///
/// - returns: The result of the action.
myVariable.withValue { currentValue in
    return false
}

/// Atomically replace the contents of the variable.
///
/// - parameters:
///   - newValue: A new value for the variable.
///
/// - returns: The old value.
let oldValue = myVariable.swap(true)
```

## License
The MIT License

Copyright (c) 2020 David Ehlen

See LICENSE file

