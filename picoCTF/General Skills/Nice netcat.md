using netcat `nc mercury.picoctf.net 49039`
- we will get a numbers list which are in ASCII
- convert that into letters and join them

---
ref
https://www.ascii-code.com/

---
we can write easy python code for this
```python
ascii_values = [
    112, 105, 99, 111, 67, 84, 70, 123, 103, 48, 48, 100, 95, 107, 49, 116, 116, 121, 33, 95,
    110, 49, 99, 51, 95, 107, 49, 116, 116, 121, 33, 95, 51, 100, 56, 52, 101, 100, 99, 56, 125, 10
]

# Convert each ASCII value to its corresponding character
decoded_string = ''.join(chr(num) for num in ascii_values)

print("Decoded string:", decoded_string)

```
---
flag
```bash
picoCTF{g00d_k1tty!_n1c3_k1tty!_3d84edc8}
```
