# Commands Executed in This Lab

```bash

# Inside 03-create-project folder

vim hello.rb

# -> wrote:  puts "Hello, World"

git add hello.rb

git commit -m "First Commit"

```

**Output:**

```

[main 6462a5a] First Commit

 1 file changed, 1 insertion(+)

 create mode 100644 03-create-project/hello.rb

```

**Note:** No `git init` was run because we are inside an already-initialized repository.  

In a real new project, `git init` would be the very first command and this would become a **root commit**.
