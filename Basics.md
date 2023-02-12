struct <br>
ex.:

```rust
struct User{
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}
```

<br>
tuple struct <br>
struct without name field <br>
the names are not specified, so the fields are named 0 and 1 (in a case of a tuple of 2 values data) <br>
ex.:

```rust
struct Color(i32, i32)

// how to create/access
let red = Color(255, 0);
let red_value_1 = red.0;
let red_value_2 = red.1;
```

<br>
<br>

tuples <br>
it stores multiple data values in a single unit. <br>
it's like an array but with some advantages: <br>
tuples can have different types at once <br>
tuples can have different sizes at once <br>
ex.:

```rust
// tuple with 2 elements
let point = (1, 2);
```

<br>

macro <br>
macros are invokd with a "!" at the end <br>
there are pre-defined macros and custom macros <br>
<br>
examples of pre-defined macros: <br>
println! <br>
assert! <br>
<br>
customed macros: <br>
they are defined wuth the term `macro_rules!` <br>
ex.: <br>

```rust
// it takes an expression and do something with it
macro_rules! my_macro {
    ($something:expr) => {
        println!("The value of x is: {}", $something);
    }
}

// example of how to call that:
my_macro!(1);
```

<br>
impl blocks <br>
it's like implementations of methods or traits that are accessible by structs, enum or other data types. <br>
ex.:<be>

```rust
// struct example
struct Point {
    x: i32,
    y: i32,
}

// implementation example to be used by that struct
// it implements two functions
impl Point {
    fn new(x: i32, y: i32) -> Point {
        Point { x, y }
    }

    fn distance_from_origin(&self) -> f32 {
        (self.x.pow(2) + self.y.pow(2)).sqrt() as f32
    }
}

// examples de calling implementations
let point = Point::new(3, 4);
println!("Point is: ({}, {})", point.x, point.y);

let distance = point.distance_from_origin();
println!("Distance from origin: {}", distance);
```

<br>
todo: <br>
explain impl blocks <br>
explain :: <br>
explain         (self.x.pow(2) + self.y.pow(2)).sqrt() as f32 <br>
```
