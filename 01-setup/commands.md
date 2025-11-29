````md
# Lab 01 — Commands

---

## 🆔 Configure Your Git Identity

```bash
git config --global user.name "AmirKarimi1381"
git config --global user.email "email@gmail.com"
```

> Used by GitHub contributions, `git blame`, and legal authorship tracking.
> 🔗 [https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

---

## ⚙️ Set Line Ending Behavior (LF vs CRLF)

### 🐧 Recommended for Linux/macOS (DevOps, Docker, GitHub)

```bash
git config --global core.autocrlf input
git config --global core.safecrlf true
```

> Keeps repository clean using LF
> Warns if mixed line endings appear

---

### 🪟 Alternative for Windows (only if needed)

```bash
git config --global core.autocrlf true
```

> Converts LF ↔ CRLF (can pollute repo if misused)
> 🔗 [https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings](https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings)

---

## 🔍 Verify Settings

```bash
git config --global --list | grep -E 'user|core'
```

---

## 📂 Where Git Stores These Settings

| Location         | Purpose                         |
| ---------------- | ------------------------------- |
| `~/.gitconfig`   | User-level config (what we set) |
| `.git/config`    | Repo-specific overrides         |
| `/etc/gitconfig` | System-wide default             |

---

## 💡 Optional: Save as a reusable setup script

📄 `setup_git.sh` (optional starter script)

```bash
#!/bin/bash
git config --global user.name "AmirKarimi1381"
git config --global user.email "email@gmail.com"
git config --global core.autocrlf input
git config --global core.safecrlf true
git config --global init.defaultBranch main
echo "Git is configured successfully! 🚀"
```

---

## 🧠 Final Checklist

| Configuration          | Status     |
| ---------------------- | ---------- |
| Name & Email           | ✔️         |
| Safe LF behavior       | ✔️         |
| Verified with `--list` | ✔️         |
| `.gitattributes` added | ⏳ Next Lab |

---

🚀 Your Git is now clean, traceable, and DevOps-ready.

```
