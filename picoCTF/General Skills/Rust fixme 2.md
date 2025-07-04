## text walkthrough
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?,
Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).

---
## Hints & prequisites
https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html

https://www.rust-lang.org/tools/install

---
### solution
1. extract the file using `tar` cmd `tar -xvf fixme2.tar`
2. cd into `fixme2` then to `src`
3. using text editor make changes to the code

```rust
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
    // Key for decryption
    let key = String::from("CSUCKS");

    // Edit borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decryption object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return;
    }
    let xrc = res.unwrap();

    // Decrypt and append
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
    println!("{}", borrowed_string);
}

fn main() {
    // Encrypted flag values
    let hex_values = [
        "41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61",
        "25", "0d", "c4", "60", "f2", "12", "a0", "18", "03", "51", "03", "36", "05", "0e", "f9",
        "42", "5b",
    ];

    // Convert to bytes
    let encrypted_buffer: Vec<u8> = hex_values
        .iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Mutable String to store message
    let mut message = String::new();

    // Call decrypt function
    decrypt(encrypted_buffer, &mut message);
}
```
errors
```rust
// ❌ &String         → ✅ &mut String
// ❌ println!(":?")  → ✅ println!("{}", val)
// ❌ let msg = ...   → ✅ let mut msg = ...
```
4. save the file & type cmd `cargo build` & `cargo run`
5. flag time

---

## flag
![image](https://github.com/user-attachments/assets/befb5928-5105-4d9e-879d-28c0e466b33e)
```bash
picoCTF{4r3_y0u_h4v1n5_fun_y31?}
```

---
thx


