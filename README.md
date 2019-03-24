# rust-cheatsheet


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




