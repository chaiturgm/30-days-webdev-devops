# Linux Cheatsheet

Commands I practiced on Day 2. All examples were run in a scratch folder called `playground`.

## Navigation

| Command | What it does | Example |
|---------|--------------|---------|
| `pwd` | Prints the current directory path | `pwd` |
| `ls` | Lists files and folders | `ls` |
| `ls -la` | Long list, including hidden files (names starting with `.`) | `ls -la` |
| `cd <dir>` | Moves into a directory | `cd playground` |
| `cd ..` | Moves up to the parent directory | `cd ..` |
| `cd -` | Jumps back to the previous directory I was in | `cd -` |
| `cd ~` | Goes to my home directory | `cd ~` |

## Creating files and folders

| Command | What it does | Example |
|---------|--------------|---------|
| `mkdir <name>` | Creates a directory | `mkdir playground` |
| `mkdir -p a/b/c` | Creates nested directories in one go | `mkdir -p notes/week1/day2` |
| `touch <file>` | Creates an empty file | `touch notes.txt` |
| `echo "text" > file` | Writes text to a file. **Overwrites** anything already in it | `echo "hi" > file.txt` |
| `echo "text" >> file` | **Appends** text to the end of a file | `echo "bye" >> file.txt` |

## Reading files

| Command | What it does | Example |
|---------|--------------|---------|
| `cat <file>` | Prints the whole file | `cat file.txt` |
| `head <file>` | Shows the first 10 lines | `head file.txt` |
| `tail <file>` | Shows the last 10 lines | `tail file.txt` |
| `head -n 3 <file>` | Shows the first 3 lines (works with `tail` too) | `head -n 3 file.txt` |
| `less <file>` | Opens the file page by page. `Space` = next page, arrows = scroll, `q` = quit | `less file.txt` |

## Copy, move, delete

| Command | What it does | Example |
|---------|--------------|---------|
| `cp <src> <dest>` | Copies a file (creates the destination if it doesn't exist) | `cp file1.txt file2.txt` |
| `cp -r <dir> <dest>` | Copies a whole directory | `cp -r notes notes-backup` |
| `mv <src> <dest>` | Moves a file, or renames it if the destination is in the same folder | `mv file1.txt ../` (move up one level) |
| `mv old new` | Renames a file | `mv file2.txt renamed.txt` |
| `rm <file>` | Deletes a file. **No undo, no recycle bin** | `rm renamed.txt` |
| `rm -r <dir>` | Deletes a directory and everything inside it (`-r` = recursive) | `rm -r notes-backup` |

> **Careful:** always double-check the path before running `rm -r`. Run `ls` first to see what you're about to delete.

## Searching

| Command | What it does | Example |
|---------|--------------|---------|
| `grep "text" <file>` | Prints lines containing the text | `grep "hi" file.txt` |
| `grep -i "text" <file>` | Same, but ignores upper/lower case | `grep -i "HI" file.txt` |
| `grep -n "text" <file>` | Also shows line numbers | `grep -n "hi" file.txt` |
| `grep -r "text" .` | Searches every file in the current folder and below | `grep -r "hi" .` |
| `find . -name "*.txt"` | Finds files by name | `find . -name "*.txt"` |

## Permissions (chmod)

Run `ls -l` to see permissions. A line like `-rwxr-xr--` is read in three groups: **owner**, **group**, **everyone else**.

Each permission has a number:

| Permission | Letter | Number |
|------------|--------|--------|
| Read | `r` | 4 |
| Write | `w` | 2 |
| Execute | `x` | 1 |

Add the numbers up for each group. Example: read + write = 4 + 2 = **6**, and all three = 4 + 2 + 1 = **7**.

| Command | Meaning |
|---------|---------|
| `chmod +x script.sh` | Makes a file executable |
| `chmod 644 file.txt` | Owner: read/write. Group and others: read only |
| `chmod 755 script.sh` | Owner: everything. Group and others: read and execute |
| `chmod 700 secret.txt` | Only the owner can read, write or run it |

Try it:

```bash
echo 'echo "it works"' > script.sh
./script.sh            # Permission denied
chmod +x script.sh
./script.sh            # it works
```

## Getting help

| Command | What it does | Example |
|---------|--------------|---------|
| `man <command>` | Opens the manual page (press `q` to quit) | `man ls` |
| `<command> --help` | Shows a short summary of options | `ls --help` |

## Commands I want to remember

- `>` overwrites, `>>` appends
- `cd ..` goes up, `cd -` goes back
- `rm` is permanent
- Read = 4, Write = 2, Execute = 1
