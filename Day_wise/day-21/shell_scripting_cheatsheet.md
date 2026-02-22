# 🐚 Shell Scripting Cheat Sheet – Day 21

This is my personal Shell Scripting reference guide built after learning from basics to real-world projects.

It covers everything from variables to loops to text processing and debugging.

---

# 📌 Quick Reference Table

| Topic | Key Syntax | Example |
|-------|------------|---------|
| Variable | `VAR="value"` | `NAME="DevOps"` |
| Argument | `$1`, `$2` | `./script.sh arg1` |
| If | `if [ condition ]; then` | `if [ -f file ]; then` |
| For loop | `for i in list; do` | `for i in 1 2 3; do` |
| Function | `name() { ... }` | `greet() { echo "Hi"; }` |
| Grep | `grep pattern file` | `grep -i "error" log.txt` |
| Awk | `awk '{print $1}' file` | `awk -F: '{print $1}' /etc/passwd` |
| Sed | `sed 's/old/new/g' file` | `sed -i 's/foo/bar/g' config.txt` |

---

# 🔹 1. Basics

## Shebang

```bash
#!/bin/bash
```

Specifies that the script should run using Bash.

---

## Running a Script

```bash
chmod +x script.sh
./script.sh
```

Or:

```bash
bash script.sh
```

---

## Comments

```bash
# This is a comment
echo "Hello" # Inline comment
```

---

## Variables

```bash
NAME="Divyat"
echo $NAME
echo "$NAME"
echo '$NAME'
```

- `" "` → Expands variable  
- `' '` → Prints literally  

---

## Read User Input

```bash
read -p "Enter name: " NAME
echo "Hello $NAME"
```

---

## Command-Line Arguments

| Symbol | Meaning |
|--------|---------|
| `$0` | Script name |
| `$1` | First argument |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$?` | Exit status |

Example:

```bash
./script.sh hello world
```

---

# 🔹 2. Operators & Conditionals

## String Comparison

```bash
[ "$a" = "$b" ]
[ "$a" != "$b" ]
[ -z "$var" ]
[ -n "$var" ]
```

---

## Integer Comparison

```bash
-eq  # equal
-ne  # not equal
-lt  # less than
-gt  # greater than
-le  # less or equal
-ge  # greater or equal
```

---

## File Test Operators

```bash
-f file   # file exists
-d dir    # directory exists
-e file   # exists
-r file   # readable
-w file   # writable
-x file   # executable
-s file   # not empty
```

---

## If Statement

```bash
if [ condition ]; then
  command
elif [ condition ]; then
  command
else
  command
fi
```

---

## Logical Operators

```bash
command1 && command2
command1 || command2
! condition
```

---

## Case Statement

```bash
case "$var" in
  start)
    echo "Starting"
    ;;
  stop)
    echo "Stopping"
    ;;
  *)
    echo "Unknown"
    ;;
esac
```

---

# 🔹 3. Loops

## For Loop (List)

```bash
for fruit in apple mango banana
do
  echo $fruit
done
```

---

## C-Style For Loop

```bash
for ((i=1; i<=5; i++))
do
  echo $i
done
```

---

## While Loop

```bash
while [ "$num" -gt 0 ]
do
  echo $num
  num=$((num-1))
done
```

---

## Until Loop

```bash
until [ "$num" -eq 0 ]
do
  echo $num
  num=$((num-1))
done
```

---

## Loop Control

```bash
break
continue
```

---

## Loop Over Files

```bash
for file in *.log
do
  echo $file
done
```

---

## Loop Over Command Output

```bash
while read line
do
  echo $line
done < file.txt
```

---

# 🔹 4. Functions

## Define Function

```bash
greet() {
  echo "Hello"
}
```

---

## Call Function

```bash
greet
```

---

## Function Arguments

```bash
add() {
  echo $(($1 + $2))
}
add 5 10
```

---

## Return vs Echo

```bash
return 1
echo "Value"
```

---

## Local Variables

```bash
add() {
  local sum=$(($1 + $2))
}
```

---

# 🔹 5. Text Processing

## grep

```bash
grep "error" file.txt
grep -i "error" file.txt
grep -r "error" /var/log
grep -c "error" file.txt
grep -n "error" file.txt
grep -v "error" file.txt
grep -E "error|fail" file.txt
```

---

## awk

```bash
awk '{print $1}' file.txt
awk -F: '{print $1}' /etc/passwd
awk 'BEGIN {print "Start"} {print $1} END {print "Done"}' file
```

---

## sed

```bash
sed 's/old/new/g' file.txt
sed -i 's/foo/bar/g' file.txt
sed '2d' file.txt
```

---

## cut

```bash
cut -d: -f1 /etc/passwd
```

---

## sort

```bash
sort file.txt
sort -n file.txt
sort -r file.txt
sort -u file.txt
```

---

## uniq

```bash
uniq file.txt
uniq -c file.txt
```

---

## tr

```bash
echo "hello" | tr 'a-z' 'A-Z'
```

---

## wc

```bash
wc -l file.txt
wc -w file.txt
wc -c file.txt
```

---

## head / tail

```bash
head -5 file.txt
tail -5 file.txt
tail -f log.txt
```

---

# 🔹 6. Useful One-Liners

Delete files older than 7 days:

```bash
find /path -type f -mtime +7 -delete
```

Count lines in all `.log` files:

```bash
wc -l *.log
```

Replace text in multiple files:

```bash
sed -i 's/old/new/g' *.txt
```

Check service status:

```bash
systemctl is-active nginx
```

Tail logs and filter errors:

```bash
tail -f app.log | grep "ERROR"
```

---

# 🔹 7. Error Handling & Debugging

## Exit Codes

```bash
exit 0
exit 1
echo $?
```

---

## Strict Mode

```bash
set -e
set -u
set -o pipefail
set -euo pipefail
```

---

## Debug Mode

```bash
set -x
```

---

## Trap

```bash
trap 'echo "Cleaning up..."' EXIT
```

---

# 🧠 Final Notes

This cheat sheet includes:

- Variables
- Arguments
- Conditions
- Loops
- Functions
- Text processing
- Error handling
- Real-world one-liners

I’ll keep updating this as I learn more.

