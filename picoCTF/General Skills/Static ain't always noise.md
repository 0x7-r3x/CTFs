# PicoCTF — Static ain't always noise

> General Skills | Easy

---

## ⚙️ Steps

dl the script that run it
```bash
#!/bin/bash

# PicoCTF - Static ain't always noise (Auto Solver Script)

# Download challenge files
wget -q https://mercury.picoctf.net/static/ff4e569d6b49b92d090796d4631a2577/static
wget -q https://mercury.picoctf.net/static/ff4e569d6b49b92d090796d4631a2577/ltdis.sh

# Make the script executable
chmod +x ltdis.sh

# Run the script on the binary
./ltdis.sh static

# Extract and print the flag
echo -e "\nFlag found:"
grep pico static.ltdis.strings.txt
```

---

## 🏁 Flag

```
picoCTF{d15a5m_t34s3r_f6c48608}
```
