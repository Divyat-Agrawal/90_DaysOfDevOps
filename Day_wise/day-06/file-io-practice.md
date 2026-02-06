# 🐧 Day 06 – Linux File Read/Write Practice

This practice note shows basic Linux commands for creating, writing, and reading text files.

---

## 📁 Create a File

```bash
touch notes.txt
```
Creates an empty file named `notes.txt`.

---

## ✍️ Write Text to the File

```bash
echo "Learning Linux is fun" > notes.txt
```
Writes text into the file (overwrites existing content).

```bash
echo "I am practicing file commands" >> notes.txt
```
Appends a new line to the file.

---

## 🖥 Write & Display Using `tee`

```bash
echo "This line was added using tee" | tee -a notes.txt
```
Writes to the file and displays output at the same time.

---

## 📖 Read the Full File

```bash
cat notes.txt
```
Displays the entire contents of the file.

---

## 🔍 Read the First Lines

```bash
head -n 2 notes.txt
```
Shows the first two lines of the file.

---

## 🔚 Read the Last Lines

```bash
tail -n 2 notes.txt
```
Shows the last two lines of the file.

---

## ✅ What I Learned

- How to create a file  
- How to write and append text  
- How to read full or partial file content  
- How to use redirection and `tee`  

These commands are useful for logs, configuration files, and scripts in Linux.
