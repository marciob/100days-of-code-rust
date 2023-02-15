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
ex.: <br>

```rust
enum IpAddressKind {
    V4,
    V6,
}

fn main() {
    // it's using the `::` to access the enum variants
    let four: IpAddressKind = IpAddressKind::V4;
    // it's using the `::` to access the enum variants
    let six: IpAddressKind = IpAddressKind::V6;
}
```

<br>

Option Enum
it's often to be used to receive a result of a computation that might succeed or fail, or to receive an absence of a value <br>
it has two variants, the first one (called Some) is an existing value and the second one (called None) the abscense of a value <br>
ex. of Option Enum definition: <br>

```rust
// it's a generic enum, it can be used with any type
// it's part of the Rust standard library and is pre-defined
enum Option<T>{
 Some(T),
 None
}
```

ex. of Option Enum usage: <br>

```rust
let x: Option<i32> = Some(5); // create an Option<i32> value that contains the integer 5
let y: Option<i32> = None;    // create an Option<i32> value that represents the absence of a value
```

<br>

`unwrap` <br>
it's a method provided by Option and Result enums <br>
it gives a panic if the value is None <br>
a panic is like a runtime error <br>
ex.: <br>

```rust
let x = Some(5);
let y = None;

println!("The value of x is {}", x.unwrap());  // prints "The value of x is 5"
println!("The value of y is {}", y.unwrap());  // panics at runtime
```

<br>

`unwrap_or` <br>
it gives a default value to be used if the value is None <br>
ex.: <br>

```rust
let x = Some(5);
let y = None;

println!("The value of x is {}", x.unwrap_or(0));  // prints "The value of x is 5"
println!("The value of y is {}", y.unwrap_or(0));  // prints "The value of y is 0"
```

<br>

`match` <br>
it compares if a value matches a pattern and executes code based on the match <br>
it's a bit similar to a switch statement in javascript <br>
ex.: <br>

```rust
// example 1
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

// it's using the `match` to compare the value of coin
// it's a bit similar to a switch statement in javascript
// if the value is Penny, it will return 1
// if the value is Nickel, it will return 5
// if the value is Dime, it will return 10
// if the value is Quarter, it will return 25
// if the value is none of the above, it will return 0
// you need to make sure that all the possible cases are covered, otherwise it will throw an error
fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}

// example 2
fn value_in_cents2(coin: Coin) -> u8 {
    // it's using the `match` to compare the value of coin
    // if the value is Penny, it will prints "Lucky penny!" and return 1
    match coin {
        Coin::Penny => {
            println!("Lucky penny!");
            1
        },
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
        }
    }

// example 3
// you can use the `_` to match any value
// since it's using the `_`, it doesn't need to cover all the possible cases, because it will match any value
fn value_in_cents3(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        _ => 0, // it will return 0 if the value is none of the above
    }
}

// example 4
// you can use the `|` to match multiple values
// it's using all the possible values of the Coin enum
fn value_in_cents4(coin: Coin) -> u8 {
    match coin {
        Coin::Penny | Coin::Nickel => 1, // it will return 1 if the value is Penny or Nickel
        Coin::Dime | Coin::Quarter => 10, // it will return 10 if the value is Dime or Quarter
    }
}

// example 5
let x = Some(5);
let y = None;

// it's using the `match` to compare the value of x
// if the value is Some, it will print the value
// if the value is None, it will print "None"
match x {
    Some(i) => println!("The value of x is {}", i),
    None => println!("The value of x is None"),
}
```

<br>

`if`
it's a conditional statement <br>
it's different from the `match` because it's not need to match all the possible cases <br>
ex.: <br>

```rust
// example 1
let x = Some(5);
let y = None;

// it's using the `if` to compare the value of x
// it's read backwards
// if the value is Some, it will print the value
if let Some(i) = x {
    println!("The value of x is {}", i);
}

// example 2
// it's using the `if` to compare the value of y
// it's read backwards
// if the value of y is None, it will print "None"
if let None = y {
    println!("The value of y is None");
}

// example 3
let some_value: Option<i32> = Some(3);

// it's using the `if` to compare the value of some_value
// it's read backwards
// if the value of some_value is Some(3), it will print "three"
if let Some(3) = some_value {
    println!("three");
}
```

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
