## text walkthrough
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?,
Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).

---
## Hints & prequisites
Just read the comments

https://www.rust-lang.org/tools/install

---
### solution
1. extract the file using `tar` cmd `tar -xvf fixme3.tar`
2. cd into `fixme3` then to `src`
3. using text editor make changes to the code

```rust
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
    // Key for decryption
    let key = String::from("CSUCKS");

    // Editing our borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decryption object
    let res = XORCryptor::new(&key);
    if let Err(e) = res {
        eprintln!("Failed to create XORCryptor: {:?}", e);
        return;
    }
    let xrc = res.unwrap();

    // Decrypt the buffer
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);

    // Convert decrypted bytes to string and append
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
    
    println!("{}", borrowed_string);
}

fn main() {
    // Encrypted flag values
    let hex_values = [
        "41", "30", "20", "63", "4a", "45", "54", "76", "12", "90", "7e", "53", "63", "e1", "01",
        "35", "7e", "59", "60", "f6", "03", "86", "7f", "56", "41", "29", "30", "6f", "08", "c3",
        "61", "f9", "35",
    ];

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values
        .iter()
        .map(|&hex| {
            u8::from_str_radix(hex, 16).expect("Invalid hex value in encrypted buffer")
        })
        .collect();

    let mut party_foul = String::from("Using memory unsafe languages is a: ");
    decrypt(encrypted_buffer, &mut party_foul);
}
```
errors
```rust
Issues in the Original Code
Unnecessary unsafe Block: The unsafe block is commented out, but even if it were active, it’s unnecessary. The decrypt_vec method likely returns a Vec<u8>, which is already memory-safe. Converting it to a raw pointer and then to a slice is redundant and risky.
Potential Memory Safety Issues: The use of raw pointers and std::slice::from_raw_parts is unnecessary since Vec<u8> already provides safe access to its contents.
Error Handling: The code checks for errors when creating the XORCryptor but doesn’t provide meaningful error feedback. It silently returns, which might not be ideal for debugging.
Commented-Out Code: The commented-out unsafe block and related comments suggest incomplete or experimental code, which should be cleaned up.
Hardcoded Hex Values: The hex values are provided as strings, which is fine, but the code could validate them better to avoid runtime panics.
```
4. save the file & type cmd `cargo build` & `cargo run`
5. flag time

---

## flag

```bash
[~/Hacking/games/PicoCTF/general-skills/rust-fixme/fixme3/src] cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.01s
     Running `/home/hack/Hacking/games/PicoCTF/general-skills/rust-fixme/fixme3/target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{n0w_y0uv3_f1x3d_1h3m_411}

```
cpy
```
picoCTF{n0w_y0uv3_f1x3d_1h3m_411}
```
---
thx

