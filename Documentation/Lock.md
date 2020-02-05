# Lock

`Lock` exposes `os_unfair_lock` on supported platforms, with pthread mutex as the fallback (or for recursive locks).

``` swift
public class Lock
```

## Nested Types

  - [Lock.UnfairLock](Lock_UnfairLock)
  - [Lock.PthreadLock](Lock_PthreadLock)

## Methods

## make()

Return an instance of a `Lock`, according to API availability (`os_unfair_lock_t` or `pthread_mutex_t` based).

``` swift
public static func make() -> Lock
```

### Returns

a `Lock` instance

## lock()

Locks the lock

``` swift
public func lock()
```

## unlock()

Unlocks the lock

``` swift
public func unlock()
```

## try()

Locks the lock if it is not already locked.

``` swift
public func try() -> Bool
```

### Returns

Returns `true` if the lock was succesfully locked and `false` if the lock was already locked.
