`struct`
<br>
ex.:
<br>

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
macros are invoked with a "!" at the end <br>
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

`use` <br>
it's like "impot" <br>
allows to import items, like modules, functions, structs, enums, or traits from another scope into the current scope. <br>
ex.: <br>

```rust
// it's importing the Display trait from the fmt module in the std library scope
// now Display can be used directly without having to prefix it with "std::fmt::" every time
use std::fmt::Display;

// example of using Display directly:

struct Person {
    name: String,
    age: u32,
}

impl Display for Person {
    fn fmt(&self, f: &mut std::fmt::Formatter) -> std::fmt::Result {
        write!(f, "Person {{ name: {}, age: {} }}", self.name, self.age)
    }
}

fn main() {
    let person = Person { name: "John".to_string(), age: 30 };
    println!("{}", person);
}

```

<br>

`std` <br>
stants for "standard library" <br>
it's the default collection of modules and types included with the Rust language. <br>
ex.: <br>

```rust
use std::fmt::Display;
```

<br>

`::` <br>
it's used to refer to a function, method, or associated item that is defined in a trait. <br>
it's like the use of `.` in Javascript, but in a broader way, it allows to access more things, like namespace, static methods, etc. <br>

<br>

`pow` <br>
it's a method that returns the power of a number <br>
ex.: <br>

```rust
// Using `pow` to calculate the square of a number
let x = 2;
let square = x.pow(2); // 4

// Using `pow` to calculate the cube of a number
let y = 3;
let cube = y.pow(3); // 27

// Using `pow` to calculate the power of a number
let base = 2;
let exponent = 3;
let power = base.pow(exponent); // 8
```

<br>

`as` <br>
it converts a from one data type to another <br>
ex.: <br>

```rust
// x is being create originally as a u32
let x: u32 = 42;
// y is being created as a u8, and it's converting the value of x from u32 to u8
let y: u8 = x as u8;
```

<br>

`Display` <br>
it allows to convert a value into a string. <br>
// explain more and better

todo studies: <br>
impl Display for Person {
