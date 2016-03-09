# Setting Closure Field

Fields can be configurable in a closure by utilizing the closure's delegate.

```
static void setClosureField(closureDelegate) {
    closureDelegate.someField {
        // Some other closure under someField
    }
}

Closure cl = {
    setClosureField(delegate)
}
```

This is identical to the following Closure
```
Closure cl = {
    someField {
        //Some other closure under someField
    }
}
