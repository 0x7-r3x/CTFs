# PicoCTF — Bases

> **Challenge Prompt**
> `What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.`

---

## 🧠 Step-by-step

### 🔍 Step 1 — Analyze the string

The string looks encoded in some format — likely Base64 (common in CTFs).

---

### 🛠️ Step 2 — Decode it

Use the terminal to decode it using `base64`:

```bash
echo "bDNhcm5fdGgzX3IwcDM1" | base64 --decode
```

Or the shorter version:

```bash
echo "bDNhcm5fdGgzX3IwcDM1" | base64 -d
```

---

### 🏁 Flag

```text
picoCTF{l3arn_th3_r0p35}
```

---

## 📚 Commands used

| Command     | Description                                            |                                            |
| ----------- | ------------------------------------------------------ | ------------------------------------------ |
| `echo`      | Outputs text to the terminal                           |                                            |
| \`          | \` (pipe)                                              | Sends output from one command into another |
| `base64 -d` | Decodes Base64-encoded strings (`--decode` also works) |                                            |

> The pipe lets us feed the `echo` output directly into `base64 -d`, decoding in one line.

---

## 🧵 References

* [Base64 Encoding](https://en.wikipedia.org/wiki/Base64)
* `man base64`

---
