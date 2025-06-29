
# writeup: picoCTF - even rsa can be broken???

> category: cryptography  
> points: 200  
> difficulty: easy  
> event: picoctf 2025  
> solved by: mH4ck3r0n3  

---

## 🧠 challenge

> this service encrypts a flag using rsa  
> only n and e are given  
> connect via:  
> `$ nc verbal-sleep.picoctf.net 58750`  
> source file provided

---

## 📁 files

- `encrypt.py`
- `flag.txt` (hidden on server)

---

## 🔍 code

```python
from Crypto.Util.number import bytes_to_long, inverse
from setup import get_primes

e = 65537

def gen_key(k):
    p, q = get_primes(k//2)
    N = p * q
    d = inverse(e, (p - 1) * (q - 1))
    return (N, e), d

def encrypt(pubkey, m):
    N, e = pubkey
    return pow(bytes_to_long(m.encode()), e, N)
```

rsa key is weak  
→ small primes used  
→ n can be factored

---

## 🔓 vuln

> weak rsa:  
- primes `p`, `q` too small  
- makes factoring `n = p*q` trivial

---

## 🎯 solution path

1. extract `N` and `ciphertext` from server  
2. factor `N` → get `p`, `q`  
3. compute φ(N) = (p-1)(q-1)  
4. compute private key `d = inverse(e, φ(N))`  
5. decrypt: `m = c^d mod N`

---

## ⚙️ exploitation

used `sympy` to factor `n`  
example:

```python
from sympy import factorint

n = <from server>
factors = factorint(n)
p, q = list(factors.keys())
```

then:

```python
phi = (p - 1) * (q - 1)
d = inverse(e, phi)
m = pow(ciphertext, d, n)
```

decoded flag from int to bytes

---

## 🚩 flag

```text
picoCTF{tw0_1$_pr!m33991588e}
```

---

## 🛠️ tools

- `python3`
- `sympy`
- `netcat`
- `rsa-ctf-tool` (optional)

---

## 📚 learnings

- rsa is only secure if primes are big enough  
- private key = easy to recover if `N` is weak  
- real-world rsa should use proper keygen

---

## 📊 stats

- ⏱️ time: ~7min  
- 🌍 rank: 1537 / 9743  
- 💰 points: 200  

---

## 📎 refs

- https://github.com/Heisenberk/rsa-ctf-tool  
- https://stackoverflow.com/q/49878381  
- https://www.dcode.fr/rsa-cipher (easy solve)  

---
