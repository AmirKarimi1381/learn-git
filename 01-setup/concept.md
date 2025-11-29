# Lab 01 - Global Git Configuration & Line Endings

### Why Git needs your identity
Every single commit in Git is permanently signed with a name + email.  
This is how `git blame`, GitHub contributions, and legal authorship work.  
Set once globally -> applies to every repository forever.

### The infamous line ending war: CRLF vs LF
|--------------|-------------|--------------------|-------------------------------------------------------------|
| System       | Line ending | Bytes              | Historical reason                                           |
|--------------|-------------|--------------------|-------------------------------------------------------------|
| UnixBaseOS   | LF          | `\n` (0x0A)        | Original UNIX standard from 1970s                           |
| Windows      | CRLF        | `\r\n` (0x0D 0x0A) | Inherited from old typewriter "Carriage Return + Line Feed" |
|--------------|-------------|----------------------------------------------------------------------------------|

**Open-source world standard = LF only**  
99.9 % of GitHub/GitLab repositories store text files with pure LF.  
This is enforced by most linters, CI systems, and editors in 2025.

### What happens if you ignore this?
- Git sees every line as changed -> fake 100 % diffs
- Scripts break on Linux (`\r` interpreted as part of filename/command)
- `git blame` becomes useless noise
- CI/CD pipelines fail on macOS/Linux containers
- Teammates hate you forever

### The perfect solution (2025 best practice)
Meaning:
On commit   -> automatically convert CRLF -> LF (keeps repository clean)
On checkout -> leave files untouched (stay as LF, perfect for Unix)

```bash
git config --global core.safecrlf true
```

Extra safety -> Git will warn or reject if someone tries to commit inconsistent line endings.

**Golden rule for real-world teams**
Always add a ```.gitattributes``` file at repository root:
```gitattributes
# Normalize all text files to LF in the repository
* text=auto eol=lf
```
This file is committed once and forces correct behavior for everyone --- even if they have wrong global config.

***Summary table***
|--------------------|-------------|--------------------|-------------------------------------------------------------|
|Setting             | UnixBaseOS  | Windows            | Repository stays clean?       | Recommended?                |
|--------------------|-------------|--------------------|-------------------------------------------------------------|
|core.autocrlf false | NO          | NO                 | Only if everyone is perfect   | Never                       |
|--------------------|-------------|--------------------|-------------------------------------------------------------|
|core.autocrlf input | YES         | NO                 | YES                           | YES (Unix)                  |
|--------------------|-------------|--------------------|-------------------------------------------------------------|
|core.autocrlf true  | NO          | YES                | YES                           | YES (Windows)               |
|--------------------|-------------|--------------------|-------------------------------------------------------------|
|.gitattributes      | YES         | YES                | YES Forever                   | Golden Standard             |
|--------------------|-------------|--------------------|-------------------------------------------------------------|
+ .gitattributes * text=auto eol=lf

Now your Git is ready for serious DevOps work.
