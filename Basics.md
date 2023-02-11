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
todo: <br>
explain what is macro <br>
explain println <br>
explain impl blocks <br>
