# Time Machine – picoCTF 2024

**Author:** 0x7_r3x
**Points:** 50

---

## Description

> What was I last working on? I remember writing a note to help me remember…
> You can download the challenge files here: []()

Hints:
- `cat` won't help here.
- Git is the key. Read the [Git section in picoPrimer](https://primer.picoctf.org/#_git_version_control).
- When committing a file with git, a message can (and should) be included.

---

## Solution

The challenge revolves around **Git commit messages**.

### Step-by-step:

1. unzip the zip file with `unzip` command
2. cd to the `drop-in` directory (Inside that directory there's a file, but that file is not the flag.)
3. using ```git init``` command you to initialize
4. we can check the commit message because the hint give a direct clue where's the flag.
     To check the commit message, we can use this command:
     `git log`
---
## Flag
As you can see from the video below, the flag is literally in git commit message
[![asciicast](https://asciinema.org/a/dRmIb7c3FzUFxNO8AMsWEkWFK.svg)](https://asciinema.org/a/dRmIb7c3FzUFxNO8AMsWEkWFK)
```
picoCTF{t1m3m@ch1n3_8defe16a}
```

