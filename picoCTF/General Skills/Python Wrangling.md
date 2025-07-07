# PicoCTF — Python Wrangling

> General Skills | Easy

---

## 📦 Files

- `ende.py` – Python script (handles encoding/decoding)
- `flag.txt.en` – Encrypted flag file
- `pw.txt` – Password required to decrypt

---

## ⚙️ Steps

```
# 1. Download files
wget https://mercury.picoctf.net/static/01e46b1ce3d22679c37c7a8d57e14fbf/ende.py
wget https://mercury.picoctf.net/static/01e46b1ce3d22679c37c7a8d57e14fbf/flag.txt.en
wget https://mercury.picoctf.net/static/01e46b1ce3d22679c37c7a8d57e14fbf/pw.txt

# 2. Rename encrypted file (script expects 'pole.txt')
cp flag.txt.en pole.txt

# 3. Decrypt using Python script
python3 ende.py -d pole.txt
# When prompted, paste password from pw.txt
```
---
note : we did this cause If we read the souce of ende.py we can see the -d tag takes file name pole.txt

---
## 🏁 Flag

![image](https://github.com/user-attachments/assets/9c7aca94-fcec-48e7-90f6-b72765aafb51)

```bash
picoCTF{4p0110_1n_7h3_h0us3_6008014f}
```
---
