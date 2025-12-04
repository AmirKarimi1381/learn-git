# Lab 04 - Checking Status  
**Goal:** Master the most important Git command you'll ever use: `git status`

### Why `git status` is your best friend
- Tells you exactly what Git sees right now
- Shows untracked, staged, and committed files
- Prevents 99% of Git mistakes
- You`ll run it hundreds of times per day (no exaggeration!)

### The three main states we saw

| Command                          | Result                                    | Meaning                              |
|----------------------------------|-------------------------------------------|--------------------------------------|
| After creating files             | `Untracked files`                         | Git sees them but doesn't track yet  |
| After `git add README.md`        | `Changes to be committed` + untracked     | Ready for commit + some ignored      |
| After full commit                | `nothing to commit, working tree clean`  | Perfect! Everything is saved         |

### Golden Rule
**When in doubt -> `git status`**  
**Still in doubt -> `git status` again**

You now officially know the #1 most used Git command in the world!
