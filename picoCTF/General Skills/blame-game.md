## Rust-fixme1 CTF game walkthrough

**Challenge**: [here](https://play.picoctf.org/practice/challenge/405?category=5&difficulty=1&page=1)
**author**: 0x7\_r3x

---

## 📹 Video


---

## 🧾 Text Walkthrough

### Steps:

1. Download the challenge file using:

   ```bash
   wget https://artifacts.picoctf.net/c_titan/159/challenge.zip
   ```
2. Unzip the downloaded file:

   ```bash
   unzip challenge.zip
   ```
3. Move into the extracted directory:

   ```bash
   cd drop-in/
   ```
4. We are told the program isn’t working and need to find out *who* is responsible.
5. A normal `git log` is not enough since the repo has many changes.
6. Narrow down the investigation to a specific file suspected in the issue:

   ```bash
   git log message.py
   ```
7. Look through the commit messages to identify suspicious changes.
8. Find the commit with message:

   ```
   optimize file size of prod code
   ```
9. The author of this commit is the flag.

---

### 🏁 Flag

```
picoCTF{@sk_th3_1nt3rn_81e716ff}
```

---

### 📚 References

* Challenge: [url](https://play.picoctf.org/practice/challenge/405?category=5&difficulty=1&page=1)
* Git Log Reference: [https://git-scm.com/docs/git-log](https://git-scm.com/docs/git-log)
* You can use python3 <file>.py to try running the code, though you won't need to for this challenge.

---