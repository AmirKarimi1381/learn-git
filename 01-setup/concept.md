<div align="center">

# Git Line Endings Explained Forever (LF vs CRLF)

<img src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png" width="120" alt="Git Logo" />

**Come sit next to me — I'm going to explain the whole CRLF/LF mess in the simplest way possible so you’ll never have to think about it again.**

[![GitHub stars](https://img.shields.io/github/stars/AmirKarimi1381/learn-git?style=social)](https://github.com/AmirKarimi1381/learn-git)

</div>

---

### The Problem in One Sentence

Different operating systems use different **invisible** characters to mark the end of a line:

| OS            | End-of-line sequence | Characters |
|---------------|----------------------|------------|
| Linux / macOS | LF                   | `\n`       |
| Windows       | CR + LF              | `\r\n`     |

When people on different OSes work on the same repo **without proper settings** → chaos ensues:
- Ugly `^M` characters appear in files
- Git thinks the **entire file** changed on every commit
- Diffs become unreadable, merges fail, blame is broken

### The Permanent Fix (Run Once & Forget Forever)

```bash
git config --global core.autocrlf input
git config --global core.safecrlf true
