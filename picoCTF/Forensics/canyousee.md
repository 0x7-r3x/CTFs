# PicoCTF — [canyousee](https://play.picoctf.org/practice/challenge/408?category=4&difficulty=1&page=1&solved=0)

> Forensics | Easy

---
dl files
[here](https://artifacts.picoctf.net/c_titan/129/unknown.zip)

---

## 🧠 Steps

### 🖼️ Step 1 — Open image in EXIF viewer

Uploaded the image to [EXIF](https://exifmeta.com/) (an online EXIF and analysis tool).

---

### 🔍 Step 2 — Look at metadata

Found this in the `attributionURL` field:

```
cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg==
```

---

### 🛠️ Step 3 — Decode Base64

```bash
echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg==" | base64 -d
```

---

## 🏁 Flag

```text
picoCTF{ME74D47A_HIDD3N_d8c381fd}
```

---

> 📌 Tip: You can often find flags hidden in metadata — try EXIF tools like `exiftool`, AperiSolve, or even basic `strings`.
