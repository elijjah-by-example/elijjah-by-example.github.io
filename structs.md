# Structures

There are two types of `structs` in **Elijjah**.  One is the normal struct, which is always allocated on the stack. It is declared like this:

```
class struct Person {
    var name: String
    var age:  Integer8
}
```

Use it as so:

```
class Main {
    main() {
        val p = Person()
        p.name = "Peter"
        p.age  = 28
    }
}
```

## Anonymous structs

The other type of struct is returned from a function when multiple (named) results are desired.

```
class Main {
    open(f: FileName) -> (handle: FileHandle, error: Error) {
        abstract
    }

    main() {
        const (handle, error) = open(FileName("foo"))
        if (!error) {
            with (handle) {
                handle.write("bar")
            }
        }
    }
}
```
