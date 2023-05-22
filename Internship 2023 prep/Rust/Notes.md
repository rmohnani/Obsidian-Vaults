`fn` is used to denote function.
`main` function is always first run.
`!` postfix means macro
`let` used to declare variables which are immutable by default
`mut` is required to be able to make variable mutable
- references are immutable by default. So even if we have `let mut guess`,
`&guess` is still immutable. When passing a reference as argument to a function expecting it to modify the reference we need to pass it `&mut guess`
- `read_line` returns a `Result` type value. Result is an enumeration meaning in can be in one of possible variant states. `Result`'s variants are `Ok` and `Err`
- If `Result` is `Err` program will panic with message.
- `println!("You guessed: {guess}");` can print guess variable
- for multiple use `println!("{} {}", x, y)`
- `start..=end` is a Range type object which is inclusive on start and end
- `thread_rng` is a particular random number generator in rand
- `Ordering` is enum with variants `Less, Greater, Equal`
- `match` expression contains arms. each arm consists of a pattern to match against.
- `const` used to declare constants. cannot be used with mut. necessarily immutable. must be type annotated and must be set to constant expression not one that can be determined at runtime
- can shadow old variable with new variable of the same name
- `mut` can't be used to change a variable's type, simply shadow instead with another `let`
- `char` literals specified with single quotes. string literals with double quotes.
- value and type of a tuple without any values has a special name unit is represented by `()`.
- unlike tuples every element of an array must have the same type
- vector is similar to an array except its allowed to grow and shrink while an array's size is fixed
- array's type is `[element_type; array_length]`
- can initialize array to same value by `[initial_value; array_length]`
- When you attempt to access an element using indexing, Rust will check that the index you’ve specified is less than the array length. If the index is greater than or equal to the length, Rust will panic. This check has to happen at runtime, especially in this case, because the compiler can’t possibly know what value a user will enter when they run the code later.
   This is an example of Rust’s memory safety principles in action. In many low-level languages, this kind of check is not done, and when you provide an incorrect index, invalid memory can be accessed. Rust protects you against this kind of error by immediately exiting instead of allowing the memory access and continuing.
- 