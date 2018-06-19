# Rust in Production
## Verbose vs Composable
### J Haigh
### @DebugSteven

---

## About Me
- Bachelor's in CS from CU Denver |
- Self studied Haskell |
- 1 Month as a Full Time Rust Developer |
- 1 Small Rust Project before |

---

## Haskell
## +
## C++

---

## Big Projects can be
## Difficult to Approach

130,000 lines of Rust code
[Cargo Count by kbknapp](https://github.com/kbknapp/cargo-count)

---

## But Rust has good tools!

IntelliJ type inference
Rust Racer Vim plugin
Great compiler errors with examples!
Lots of examples & docs online

---

### Type Inference in IntelliJ
[Inference](intellij.png)

---

### Compiler Error & More Info
[Error1](error1.png)

---

### Compiler Error & More Info
[Error2](error2.png)

---

### Compiler Error & More Info
[Error3](error3.png)

---

## Flexible & Inclusive

Note:
Request For Comments for new language features.
The pipes in front of the match expressions
I think is pretty cool & it looks a lot like Haskell.
Impl Trait is something that is seems to be inspired by Go. 
This is one of my fav things about Rust, but the downside is that you can write your
code in so many different ways. It can be difficult for a newcomer to your
codebase to get acquainted with it quickly.

---

## if let

```rust
let optional = Some(7);

match optional {
    Some(i) => {
        println!("This is a really long string and `{:?}`", i);
    },
    _ => {},
};
```
Note:
We just care about the some case & then we use the value.

+++

## if let
```rust
let optional = Some(7);

if let Some(i) = optional {
    println!("We can print our some value: {:?}", i);
}
```

---

## ?

```rust
fn we_care_about_ok(v: i32) -> Result<i32, &'static str> {
    if v != 3 {
        Ok(v)
    } else {
        Err("The value for v is 3 & that's not ok")
    }
}

let value = match we_care_about_ok(4) {
    Ok(v) => println!("Our value {}!", v),
    Err(e) => println!("error: {}", e),
};
```

+++

```rust
fn we_care_about_ok(v: i32) -> Result<i32, &'static str> {
    if v != 3 {
        Ok(v)
    } else {
        Err("The value for v is 3 & that's not ok")
    }
}

let value = we_care_about_ok(4)?; 
```

---

## map

```rust
fn business_logic(good_var_name: BusinessType) -> BusinessType {
    // top secret
}

fn business_process(j: Option<BusinessType>) -> Option<BusinessType> {
    j.map(business_logic)
}
```
