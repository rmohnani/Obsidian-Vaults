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
- 
