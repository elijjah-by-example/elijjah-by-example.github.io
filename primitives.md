# Primitives

Elijjah provides access to a wide variety of `primitives`. A sample includes:


### Scalar Types

* signed integers: `Integer8` (`i8`), `Integer16`(`i16`), `Integer32`(`i32`), `Integer64`(`i64`), `i128` (not really) and `SystemInteger`
* unsigned integers: `Unsigned8` (`u8`), `Unsigned16`(`u16`), `Unsigned32`(`u32`), `Unsigned64`(`u64`), `u128` (not really) and `SystemUnsigned`
* `usize`and `isize`: If you want a pointer, just use `Pointer`. This is not to be confused with `C.Pointer` (I don't know how though...)  There is also the `Opaque` type, which must be cast to be used.
* floating point: `Float32`(`f32`), `Float64`(`f64`)
* `Character` An 8-bit unigned value. Note there is `Character8` and `Character16` and `Character32` (aka `Unicode`)
* `Unicode` Unicode scalar values like `'a'`, `'α'` and `'∞'` (4 bytes each)
* `Boolean` either `True` or `False`. There are `true` and `false` aliases for those that want them.
* and the unit type `Unit`, which has no value. It is meant to be used as a function return type. There is also `NoneType`, the only value of which is `None`, which is aliased to `null`.

Note that the short names are borrowed from **Rust** and are [**alias**](alias.md)es to the longer names.

Note that arbitrary precision arithmatic should be possible, I just haven't decided how yet. (Like a `BigDecimal` class.)


### Compound Types

* lists like `[1, 2, 3]`
//* tuples like `(1, true)`
* dictionaries (hash maps) like `\`{'one': 1, 'two': 2, 'three': 3}`

Arrays are not provided for with special syntax as of right now and neither are tuples.

Variables can always be *type annotated*. Numbers may additionally be
annotated via a *suffix* (another feature borrowed from Rust) or *by default*. Integers default to `SystemInteger` and
floats to `SystemFloat` (which will usually turn out to be `Float64`). Note that Elijjah can also deduce types from how they are used.

```java,editable,ignore,mdbook-runnable
class Main {
  main() {
    // Variables can be type annotated.
    val logical: Boolean = true;

    val a_float: f64 = 1.0;  // Regular annotation
    val an_integer   = 5i32; // Suffix annotation

    // Or a default will be used.
    val default_float   = 3.0; // `SystemFloat`
    val default_integer = 7;   // `SystemInteger`
    
    // A type can also be inferred from context 
    var inferred_type = 12; // Type SystemInteger is deduced fromm this line
    inferred_type = 4294967296i64; // Type i64 is deduced from this line. Lets hope they are compatible, otherwise the compiler throws an error
    
    // A mutable variable's (var) value can be changed.
    var mutable = 12; // Mutable `i32`
    mutable = 21;
    
    // Error! The type of a variable can't be changed.
    mutable = true;
    
    // Variables can (not) be overwritten with shadowing.
    let mutable = true;
  }
}
```

// ### See also:

// [the `std` library][std], [`mut`][mut], [inference], and [shadowing]

// [std]: https://doc.rust-lang.org/std/
// [mut]: variable_bindings/mut.md
// [inference]: types/inference.md
// [shadowing]: variable_bindings/scope.md

