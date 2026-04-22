# Day 01 — Viewing, Editing, Compressing, and Searching Files

## Learning goals

By the end of this lesson, you should be able to:

- inspect files with `cat`, `less`, `head`, and `tail`
- understand when compressed files are useful
- work with `.gz` files using `gzip`, `gunzip`, `zcat`, and `zless`
- edit text files with `nano`
- search text with `grep`
- combine commands using pipes (`|`)

## Working assumption

This lesson assumes the repository was cloned into the home directory:

```bash
cd ~/2026-Workshop-HSPA-Morocco/day_01
```

## 1. Create a safe text practice area

```bash
mkdir -p linux_text_practice
cd linux_text_practice
```

Create a small text file:

```bash
printf "sample_1\nInfluenza A\nSARS-CoV-2\nBioinformatics workshop\n" > notes.txt
```

Check that the file exists:

```bash
ls -lh
```

## 2. View file contents

Display the whole file:

```bash
cat notes.txt
```

Open it page by page:

```bash
less notes.txt
```

Show only the first lines:

```bash
head notes.txt
```

Show only the last lines:

```bash
tail notes.txt
```

### Questions

- When is `less` better than `cat`?
- How do you quit `less`?
- Which commands are best for very large files?

## 3. Create and edit files with nano

Create a new file and open it in `nano`:

```bash
touch my_text_file.txt
nano my_text_file.txt
```

Inside `nano`, try the following:

- write two or three lines
- save with `Ctrl + O`
- exit with `Ctrl + X`

Show the result:

```bash
cat my_text_file.txt
```

### Useful nano shortcuts

- `Ctrl + O` — save
- `Ctrl + X` — exit
- `Ctrl + W` — search
- `Ctrl + K` — cut a line
- `Ctrl + U` — paste

## 4. Compression with gzip

Make a compressed copy of your file:

```bash
cp notes.txt notes_copy.txt
gzip notes_copy.txt
ls -lh
```

Uncompress it again:

```bash
gunzip notes_copy.txt.gz
ls -lh
```

### Questions

- What changed in the file size?
- Why is compression useful in bioinformatics?

## 5. Work with gzipped files without unpacking them

Compress the file again:

```bash
gzip notes_copy.txt
```

Now inspect it in different ways:

```bash
cat notes_copy.txt.gz
```

The output above is not human-readable because the file is compressed.

Use the gzip-aware tools instead:

```bash
zcat notes_copy.txt.gz
zcat notes_copy.txt.gz | head
zcat notes_copy.txt.gz | tail
zless notes_copy.txt.gz
```

### Questions

- What is the difference between `cat` and `zcat` on a `.gz` file?
- When would `zless` be useful?

## 6. Search text with grep

Search for a word in a text file:

```bash
grep "Influenza" notes.txt
```

Count matching lines:

```bash
grep -c "Influenza" notes.txt
```

Search case-insensitively:

```bash
grep -i "bioinformatics" notes.txt
```

Search for lines that start with a pattern:

```bash
grep "^sample" notes.txt
```

### Questions

- What does `-c` do?
- What does `-i` do?
- What does `^sample` mean?

## 7. Combine commands with pipes

A pipe sends the output of one command into the next command.

Examples:

```bash
cat notes.txt | wc -l
```

```bash
grep "Bioinformatics" notes.txt | less
```

```bash
zcat notes_copy.txt.gz | head
```

### Questions

- Why is `|` useful?
- Which part runs first in `zcat notes_copy.txt.gz | head`?

## 8. Optional bioinformatics example with FASTQ

If the repository contains a practice FASTQ file such as `data/ERR10453087.fastq.gz`, you can inspect it like this:

```bash
cd ~/2026-Workshop-HSPA-Morocco/day_01
cp ../data/ERR10453087.fastq.gz ./linux_text_practice/
cd linux_text_practice
```

View the first records without unpacking the file permanently:

```bash
zcat ERR10453087.fastq.gz | head -n 12
```

Search for a sequence motif:

```bash
zcat ERR10453087.fastq.gz | grep "AACACC"
```

Count matching lines:

```bash
zcat ERR10453087.fastq.gz | grep -c "AACACC"
```

Estimate the number of FASTQ headers:

```bash
zcat ERR10453087.fastq.gz | grep -c "^@"
```

### Discussion

- What are the four lines of a FASTQ record?
- Why is counting `^@` only an estimate and not a perfect parser?

## 9. Mini challenge

In `linux_text_practice`, do the following:

1. create a file called `animals.txt`
2. add three animal names
3. compress it
4. display the first lines without unzipping it
5. count how many lines contain the letter `a`

One possible solution:

```bash
printf "cat\ndog\nzebra\n" > animals.txt
gzip animals.txt
zcat animals.txt.gz | head
zcat animals.txt.gz | grep -c "a"
```

## Quick reference

| Command | Purpose |
| --- | --- |
| `cat` | Print a file to the terminal |
| `less` | View a file page by page |
| `head` | Show the first lines |
| `tail` | Show the last lines |
| `nano` | Edit a text file in the terminal |
| `gzip` | Compress a file |
| `gunzip` | Uncompress a `.gz` file |
| `zcat` | Print the contents of a `.gz` file |
| `zless` | View a `.gz` file page by page |
| `grep` | Search for matching text |
| `grep -c` | Count matching lines |
| `|` | Send output from one command to another |