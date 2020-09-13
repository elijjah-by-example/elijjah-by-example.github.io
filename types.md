# Type

Another type of type is introduced by the `type` keyword. It allows the creation of a type 
which may be one of a few different variants. 

<!-- Any variant which is valid as a `struct` 
is also valid as an `enum`. -->

```editable
namespace {
    // Create an `enum` to classify a web event. Note how both
    // names and type information together specify the variant:
    // `PageLoad != PageUnload` and `KeyPress(char) != Paste(String)`.
    // Each is different and independent.
    type WebEvent {
        // An `type` may either be `unit-like`,
        PageLoad
    |   PageUnload,
        // like tuple structs,
    |   KeyPress(char),
    |   Paste(String),
        // or c-like structures.
<!--    |   Click { x: i64, y: i64 }, -->
    }

    // A function which takes a `WebEvent` enum as an argument and
    // returns nothing.
    inspect(event: WebEvent) {
        match event {
            WebEvent.PageLoad    { println("page loaded")   }
            WebEvent.PageUnload  { println("page unloaded") }
            // Destructure `c` from inside the `enum`.
            WebEvent.KeyPress(c) { println("pressed '{}'.", c) }
            WebEvent.Paste(s) => println("pasted \"{}\".", s) }
            // Destructure `Click` into `x` and `y`.
 //           WebEvent.Click { x, y } => {
 //               println!("clicked at x={}, y={}.", x, y);
 //           },
        }
    }

}

class Main {
    main() {
        val pressed = WebEvent.KeyPress('x');
        // `to_owned()` creates an owned `String` from a string slice.
        val pasted  = WebEvent.Paste("my text".to_owned());
        //val click   = WebEvent::Click { x: 20, y: 80 }; 
        val load    = WebEvent.PageLoad;
        val unload  = WebEvent.PageUnload;

        inspect(pressed);
        inspect(pasted);
        //inspect(click);
        inspect(load);
        inspect(unload);
    }
}
```
