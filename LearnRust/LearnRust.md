# Learn Rust

## Task 13 Challenge

"M3I6r2IbMzq9" is the text.

The text is encrypted with:

plaintext -> ROT13 -> base64 -> rot13

- Decrypt using ROT13 → base64 → Rot13 → plaintext in Rust

```rust
use std::str;

use base64::engine::general_purpose;
use base64::Engine;

use cipher_crypt::{Rot13};

fn main(){
    let text: &str = "M3I6r2IbMzq9";

    let decrypt_rot13 = Rot13::decrypt(text);

    let base64_decode = general_purpose::STANDARD.decode(&decrypt_rot13);
    println!("{}", decrypt_rot13);

    println!("{:?}", base64_decode);

    let result = match base64_decode{
        Ok(bytes) =>{
            match str::from_utf8(&bytes) {
                Ok(decoded_str) => decoded_str.to_string(),
                Err(e) => panic!("Invalid utf8 sequence: {}", e),
            }
        }
        Err(e) => panic!("Base64 failed {}", e),
    };

    println!("{}", result);

    let final_result = Rot13::decrypt(&result);

    println!("{}", final_result);
}
```

- Note that in the Cargo.TOML file the following crates need to be added:
```toml
[dependencies]
cipher-crypt = "0.18.0"
base64 = "0.22.1"
```
