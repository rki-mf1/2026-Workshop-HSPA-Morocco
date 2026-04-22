# Day 01 — Linux Basics, Navigation, and File Management

## Learning goals

By the end of this lesson, you should be able to:

- open and use the terminal comfortably
- understand the current working directory
- move through the filesystem with `cd`
- understand `~`, `.`, `..`, absolute paths, and relative paths
- create, copy, move, rename, and remove files and directories
- read built-in command documentation with `man` and `--help`

## Working assumption

This lesson assumes students cloned the repository into their home directory:

```bash
git clone https://github.com/rki-mf1/2026-Workshop-HSPA-Morocco.git
cd ~/2026-Workshop-HSPA-Morocco
```

All examples below use paths relative to that location.

## Before you start

Open a terminal and move into the workshop repository:

```bash
cd ~/2026-Workshop-HSPA-Morocco
```

Check where you are:

```bash
pwd
```

## 1. Your first commands

List the contents of the current directory:

```bash
ls
```

Try a few common variants:

```bash
ls .
ls ..
ls -l
ls -lh
ls -lt
```

### Questions

- What is the difference between `ls`, `ls -l`, and `ls -lh`?
- What does `ls ..` show?
- Which option sorts by modification time, newest first?

## 2. Getting help

Most commands provide built-in documentation.

```bash
man ls
```

Or use the short help page:

```bash
ls --help
cp --help
mv --help
rm --help
```

### Questions

- Which `ls` option shows human-readable file sizes?
- Which `cp` option lets you copy directories recursively?

## 3. Useful terminal habits

Try these shortcuts:

- Press the **Up Arrow** to reuse previous commands.
- Type `cle` and press **Tab**.
- Start typing `cd ~/2026` and press **Tab** for autocompletion.

Linux is case-sensitive:

- `clear` works
- `CLEAR` does not

Avoid spaces in file names when possible.

## 4. Moving around the filesystem

Start in the repository root:

```bash
cd ~/2026-Workshop-HSPA-Morocco
pwd
```

Now try the following:

```bash
cd day_01
pwd

cd ..
pwd

cd ~
pwd

cd ~/2026-Workshop-HSPA-Morocco/day_01
pwd

cd -
pwd
```

### Key ideas

- `~` = your home directory
- `.` = the current directory
- `..` = the parent directory
- `cd -` = the directory you were in previously

## 5. Absolute and relative paths

An **absolute path** starts from the filesystem root `/`.

Example: `/home/username/2026-Workshop-HSPA-Morocco/day_01`

A **relative path** starts from where you are right now.

Example workflow:

```bash
cd ~/2026-Workshop-HSPA-Morocco
ls day_01

cd day_01
ls .
ls ..
```

### Practice

Run these commands and explain why they work:

```bash
cd ~/2026-Workshop-HSPA-Morocco
ls day_01

cd day_01
ls ../day_02

cd ..
cd ./day_01
```

## 6. Create a safe practice area

To avoid modifying teaching materials, create a scratch directory for practice:

```bash
cd ~/2026-Workshop-HSPA-Morocco/day_01
mkdir -p linux_practice
cd linux_practice
pwd
```

## 7. Create files and directories

Create a few files and folders:

```bash
touch notes.txt
touch copy_me.txt
mkdir drafts
mkdir results
ls -lh
```

Add text to a file:

```bash
echo "Hello Bioinformatics" > notes.txt
cat notes.txt
```

Append another line:

```bash
echo "Linux is powerful." >> notes.txt
cat notes.txt
```

### Questions

- What is the difference between `>` and `>>`?
- Why is it useful to keep practice work in a separate directory?

## 8. Copy files

Copy a file into another file:

```bash
cp copy_me.txt copy_me_backup.txt
ls
```

Copy a file into a directory:

```bash
cp notes.txt drafts/
ls drafts
```

Copy a directory recursively:

```bash
cp -r drafts drafts_copy
ls
```

## 9. Move and rename files

Move a file into another directory:

```bash
mv copy_me_backup.txt results/
ls results
```

Rename a file:

```bash
mv copy_me.txt renamed_file.txt
ls
```

Move and rename at the same time:

```bash
mv renamed_file.txt drafts/final_notes.txt
ls drafts
```

## 10. Remove files and directories

Remove a file:

```bash
rm drafts/final_notes.txt
ls drafts
```

Remove an empty directory:

```bash
rmdir results
```

Remove a directory and everything inside it:

```bash
rm -r drafts_copy
```

Be careful with `rm`. Deleted files are usually not easy to recover.

## 11. Mini challenge

Complete the following workflow:

```bash
cd ~/2026-Workshop-HSPA-Morocco/day_01/linux_practice
mkdir my_tmp_dir
cp notes.txt my_tmp_dir/
mv my_tmp_dir copied_notes
ls -R
```

Now answer:

- Which object was created?
- Which command copied data?
- Which command renamed data?

## 12. Clean up

If you want to remove your practice directory at the end:

```bash
cd ~/2026-Workshop-HSPA-Morocco/day_01
rm -r linux_practice
```

## Quick reference

| Command | Purpose |
| --- | --- |
| `pwd` | Show current directory |
| `ls` | List files and folders |
| `cd` | Change directory |
| `man <command>` | Open the manual |
| `<command> --help` | Show short help |
| `touch` | Create an empty file |
| `mkdir` | Create a directory |
| `cp` | Copy files or directories |
| `mv` | Move or rename files or directories |
| `rm` | Remove files |
| `rm -r` | Remove directories recursively |
| `rmdir` | Remove an empty directory |

## Next tutorial

Continue with **Day 01 — Viewing, Editing, Compressing, and Searching Files**.
