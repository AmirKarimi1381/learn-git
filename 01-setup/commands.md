# Commands – Git Setup & Line Endings

### Run once (Linux/macOS – recommended 2025)
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

git config --global core.autocrlf input
git config --global core.safecrlf true

git config --global init.defaultBranch main
```

### Windows users
```bash
git config --global core.autocrlf true
```

### Verify
```bash
git config --global --list
```

### Must add to every repository (root)
`.gitattributes`
```
* text=auto eol=lf
```

### Quick setup script (optional)
```bash
curl -sL https://raw.githubusercontent.com/amir-sinic/git-learning/main/01-Setup/setup.sh | bash
```

**Checklist**
- [ ] Identity configured
- [ ] Line endings set to `input` (or `true` on Windows)
- [ ] `.gitattributes` added to new projects
