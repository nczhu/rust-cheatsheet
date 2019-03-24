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
* [Vector](): collection, heap (dynamic array)
* [String](): collection, heap
* [Hash map](): collection, heap

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

## Testing

#### Example
```
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
* `-- --nocapture`: shows printlns
* `-- --test-threads=1`: suppresses test concurrency
* `-- --ignored`: only runs ignored tests
* `--test` *filename*: only runs integration tests




