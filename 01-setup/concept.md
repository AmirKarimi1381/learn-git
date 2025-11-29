````md
# Lab 01 — Global Git Configuration & Line Endings

---

## 🆔 Why Git Needs Your Identity

Every commit in Git is permanently linked to a **name** and **email**.  
This powers critical features like:

- `git blame`
- GitHub contribution graphs
- Legal authorship tracking

You set it **once globally**, and it applies to **every repository forever**.

---

## ⚔️ The Line Ending War: CRLF vs LF

| System       | Line Ending | Bytes         | Historical Reason                                               |
|--------------|-------------|---------------|------------------------------------------------------------------|
| Unix / Linux | LF          | `\n` (0x0A)    | Original UNIX standard from the 1970s                          |
| Windows      | CRLF        | `\r\n` (0x0D 0x0A) | From old typewriters: *Carriage Return + Line Feed*     |

> **Open-source world standard = LF only**  
> 99.9% of GitHub/GitLab repositories store text files using **pure LF**.  
> Enforced by modern editors, CI pipelines, and Docker containers (2025).

---

## ❗ What Happens If You Ignore This?

- Git shows **fake 100% diffs** (every line looks changed)
- Shell scripts break on Linux/macOS (`\r` gets treated as part of command)
- `git blame` becomes noisy and useless
- CI/CD pipelines fail in containers
- Your teammates silently hate you

---

## 🛠️ 2025 Best Practice: The Perfect Fix

💡 Goal:  
- On **commit** → Convert `CRLF → LF` (keep repository clean)  
- On **checkout** → Leave files untouched (stay LF — safe for Unix)

```bash
git config --global core.safecrlf true
````

> Enables warnings or rejection when inconsistent line endings are detected.

---

## 🌍 Golden Rule for Real Teams — Always Use `.gitattributes`

Create this file **at the repository root**:

```gitattributes
# Normalize all text files to LF in the repository
* text=auto eol=lf
```

📌 This enforces correct behavior **for everyone** —
even if their local Git config is wrong.

---

## 📋 Summary Table

| Setting               | Unix/Linux | Windows | Repository Clean?    | Recommended?      |
| --------------------- | ---------- | ------- | -------------------- | ----------------- |
| `core.autocrlf false` | ❌          | ❌       | Only if perfect team | 🚫 Never          |
| `core.autocrlf input` | ✔️         | ❌       | ✔️                   | 👍 Yes (Unix)     |
| `core.autocrlf true`  | ❌          | ✔️      | ✔️                   | 👍 Yes (Windows)  |
| `.gitattributes`      | ✔️         | ✔️      | ✔️✔️✔️ Forever       | ⭐ Golden Standard |

> Final setup:
> `+ .gitattributes — * text=auto eol=lf`

---

🚀 **Your Git is now ready for real DevOps, CI/CD, Docker, and cross-platform collaboration.**

```
