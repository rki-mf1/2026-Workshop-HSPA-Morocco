````markdown
# Day 1 – Linux Introduction & Environment Setup

## Overview

This day introduces participants to the Linux environment and command line usage, forming the foundation for all bioinformatics analyses.

All exercises are performed on the server using the shared working directory:

```bash
/mnt/work
````

---

## Schedule

| Time  | Activity                           |
| ----- | ---------------------------------- |
| 09:00 | Check-in                           |
| 09:30 | Ice-breaker and introductions      |
| 11:00 | Talk: Linux Intro                  |
| 13:00 | Icebreaker or interactive learning |
| 13:30 | Hands-On: Linux Intro              |
| 15:00 | Hands-On: Linux advanced Intro     |
| 16:45 | Wrap-up                            |

---

## Materials

### Slides

ADD

---

## Exercises

1. [Linux Basics](exercises/01_linux_basics.md)
2. [Navigation & File Handling](exercises/02_navigation_and_files.md)
3. [Advanced Intro](exercises/03_advanced_intro.md)

---

## Working environment

All commands should be executed in:

```bash
cd /mnt/work
```

Participants should **not work in home directories** to ensure reproducibility and shared access.

---


```markdown
# Exercise 01 – Linux Basics

## Objectives
- understand terminal usage
- navigate the filesystem
- run basic commands

---

## Setup

```bash
cd /mnt/work
mkdir -p training/day1
cd training/day1
````

---

## Tasks

### 1. Where am I?

```bash
pwd
```

---

### 2. List files

```bash
ls
ls -lh
```

---

### 3. Move around

```bash
cd ..
cd ~
cd /mnt/work
```

---

## Questions

* What is your current working directory?
* What is the difference between `ls` and `ls -lh`?

````

---

```markdown
# Exercise 02 – Navigation & File Handling

## Objectives
- create, move, and delete files
- inspect file contents

---

## Setup

```bash
cd /mnt/work/training/day1
````

---

## Tasks

### 1. Create directories

```bash
mkdir data results scripts
```

---

### 2. Create files

```bash
touch data/sample.txt
echo "Hello Bioinformatics" > data/sample.txt
```

---

### 3. Copy and move

```bash
cp data/sample.txt data/sample_copy.txt
mv data/sample_copy.txt results/
```

---

### 4. View files

```bash
cat data/sample.txt
less data/sample.txt
head data/sample.txt
tail data/sample.txt
```

---

### 5. Remove files

```bash
rm results/sample_copy.txt
```

---

## Questions

* What is the difference between `cp` and `mv`?
* When would you use `less` instead of `cat`?

````

---

```markdown
# Exercise 03 – Advanced Linux Intro

## Objectives
- understand permissions
- use pipes and redirection
- combine commands

---

## Setup

```bash
cd /mnt/work/training/day1
````

---

## Tasks

### 1. Permissions

```bash
ls -l
chmod 644 data/sample.txt
```

---

### 2. Pipes

```bash
cat data/sample.txt | wc -l
```

---

### 3. Redirection

```bash
echo "New line" >> data/sample.txt
```

---

### 4. Combine commands

```bash
cat data/sample.txt | grep Bioinformatics
```

---

## Questions

* What does `>>` do?
* What is the purpose of a pipe (`|`)?

````

---

```markdown
# Linux Cheatsheet

## Navigation
- `pwd` – print working directory
- `ls` – list files
- `cd` – change directory

## File operations
- `cp` – copy
- `mv` – move
- `rm` – remove

## Viewing files
- `cat`, `less`, `head`, `tail`

## Permissions
- `chmod`, `chown`

## Pipes & redirection
- `|`
- `>`
- `>>`
````
