# Lab 01 – Commands

```bash
# Identity (run once per machine)
git config --global user.name "AmirKarimi1381"
git config --global user.email "email@gmail.com"

# Line endings - Linux/macOS (recommended)
git config --global core.autocrlf input
git config --global core.safecrlf true

# Line endings - Windows (if you ever switch)
# git config --global core.autocrlf true

# Verify
git config --global --list | grep -E 'user|core'

These settings are stored in ~/.gitconfig and apply to every repository forever.
