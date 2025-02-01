# Rust Number Guessing Game

## 1. Set Up the Project

```sh
cargo new guessing_game
cd guessing_game
```

## 2. Write the Code

Replace `src/main.rs` with:

```rust
use std::io;
use rand::Rng;
use std::cmp::Ordering;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess.");

        let mut guess = String::new();
        io::stdin().read_line(&mut guess).expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {}", guess);

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```

## 3. Add Dependencies

Modify `Cargo.toml`:

```toml
[dependencies]
rand = "0.8"
```

## 4. Build and Run

```sh
cargo run
```

The program prompts the user to guess a number between 1 and 100, providing feedback after each guess. If the guess is correct, the user wins!

For more details, check the [official tutorial](https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html).
