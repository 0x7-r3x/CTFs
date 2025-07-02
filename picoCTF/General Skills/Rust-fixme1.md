## Rust-fixme1 CTF game walkthrough

Challenge : [here](https://play.picoctf.org/practice/challenge/461?category=5&difficulty=1&page=1&solved=0)

author  0x7_r3x

---
video : https://youtu.be/q3KDhS_I2Bg

---
## text walkthrough

### Steps :
1. dl the challenge file with `wget`.
2. extract the file with cmd `tar -xvzf fixme1.tar.gz`
3. make sure you have `cargo` installed you can check `cargo --version`
4. cd into `fixme1` and cd to `src`
5. type cmd `cargo build` & we get errors
6. then open the `main.rs` file in text editor and fix the code with `;` at end and `return` word & `{}` brackets at the print funtion.
7. run the cmd `cargo run`
8. we get the flag
---
### Flag

Flag : ``` picoCTF{4r3_y0u_4_ru$t4c30n_n0w?} ```
---
### reference 
 https://play.picoctf.org/practice/challenge/461?category=5&difficulty=1&page=1&solved=0

 https://doc.rust-lang.org/book/ch01-03-hello-cargo.html

 https://doc.rust-lang.org/std/macro.println.html

 https://youtu.be/q3KDhS_I2Bg
 