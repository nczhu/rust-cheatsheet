# rust-cheatsheet

## Data Types:
#### Scalar
* [int/uint](): primitive
* [float](): primitive
* [bool](): primitive
* [char](): primitive

#### Compound
* [tuple](): primitive, stack (fixed len)
* [array](): primitive, stack (fixed len)
* [slice](): reference to String, string literals, e.g. `&var[..]`
* [struct](): ownership (like oop objects)
* [enum](): ownership, for pattern matching & error handling `enum Var`
* [Vector](): ownership, heap (dynamic array), e.g. `Vec<T>`
* [String](): ownership, heap
* [Hash map](): ownership, heap

## Control Flows
* `if` `else if` `else`
* `loop` `break` `continue`
* `while`
* `for ... in ...` or `for i in (0..11)`


## Ownership
#### Rules
* Can have ONE mutable reference (in a single scope) BUT NO immutable reference, OR
* Can have multiple immutable references BUT NO mutable reference

#### Borrowing `var`
| Borrowed Ref | Owner | Heap Storage  |
| --- |:---:| ---:|
| &var| var | bytecode|


## Generics, Traits, Lifetimes
* `Generic Types`: generic placeholder for any type or function
	* `fn name<T>(..)`
  * `impl<T> SomeType<T> {..`
* `Traits`: like interfaces, defines shared methods across types
	* `impl TraitName for Type`
	* Trait bound: `pub fn foo<T: TraitName>(var: T)`
	  ```rust
	  fn foo<T, U>(t: T, u: U) -> i32
	    where T: Trait1 + Trait2,
	          U: Trait1 + Trait3  {...}
	  ```
	* `fn .. -> impl Trait1 {}`: return value has the trait

* `Lifetimes`: Every reference has a lifetime. Need to specify lifetime parameters for **functions or structs that use references**.
  * `fn foo<'a, 'b>(x: &'a str, y: &'b str) -> &'a &str {...}`
  * **Elision Rules**: hardcoded cases lifetimes are inferred, e.g. `fn one_param(s: &str) -> &str`
  * `&'static`: static lifetime that lasts entire duration of program exe

## Testing

#### Example
```rust
#[cfg(test)]
mod tests {
	use super::*;
	#[test]
	fn it_works() {
		assert_eq!(2 + 2, 4, "error msg");
  }
}
```

#### Frequently Used
* `#[should_panic(expected = "error msg")]`
* `#[ignore]`
* `assert!()`
* `assert_eq!()`
* `assert_ne!()`
* `Result<T, E>`: `Ok(())`,  `Err((String::from("error msg")))`

#### Execution
* `cargo test` *test name*
* `--lib`: run all tests in lib/file
* `-- --nocapture`: shows printlns
* `-- --test-threads=1`: suppresses test concurrency
* `-- --ignored`: only runs ignored tests
* `--test` *filename*: only runs integration tests

## Errors
* **Unrecoverable**: `panic!` macro
* **Recoverable**: `Result<T, E>` type

```rust
    enum Result<T, E> {
        Ok(T),
        Err(E),
    }
    // OR, shorthand version: 
    	f.read_to_string(&mut s)?; // short hand for "match"
    	Ok(s)
```

## Enums
#### Match 
```rust
match some_u8_value {
    Some(3) => println!("three"),
    _ => (),
}
}
```
```rust
if let Some(3) = some_u8_value {
    println!("three");
}
```

## Hash map


## Terminology
- `Path` is a way of naming an item such as a struct, function, or module.
    - `module` a way to organize a tree of pub/private fns
    - `use` a keyword to bring a path into scope
    - `pub`, a keyword to make items public
    - `pub use`, makes fns which use a path also externally usable
    - `pub mod _;` indicates it has a sub mod.
- `as` Renaming items when bringing them into scope
- `Packages`: a Cargo feature that let you build, test, and share crates. Can contain at most one lib, many binaries.
- `Crates`: a binary/executable `[main.rs](http://main.rs)` or a library `lib.rs` (made up of a tree of modules)
    - `crate roots`: `src/main.rs` and `src/lib.rs`
