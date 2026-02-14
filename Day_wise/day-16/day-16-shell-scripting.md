# 🐚 Day 16 – Shell Scripting Basics

Today I learned the fundamentals of **Bash shell scripting**, including how scripts run, how to store data, take user input, and make decisions using conditions.

---

## 🧠 Task 1 – Hello Script

### Script: `hello.sh`

```bash
#!/bin/bash
echo "Hello, DevOps!"
```

### Commands Used

```bash
chmod +x hello.sh
./hello.sh
```

### Output

```
Hello, DevOps!
```

### What happens without shebang?

If we remove `#!/bin/bash` and run `./hello.sh`, the system may not know which interpreter to use and could throw an error.
But running `bash hello.sh` will still work because we manually specify Bash.

---

## 📦 Task 2 – Variables

### Script: `variables.sh`

```bash
#!/bin/bash

NAME="Divyat"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE"
```

### Output

```
Hello, I am Divyat and I am a DevOps Engineer
```

### Single vs Double Quotes

```bash
echo '$NAME'
echo "$NAME"
```

**Output:**

```
$NAME
Divyat
```

🔹 Single quotes treat text literally
🔹 Double quotes allow variable expansion

---

## ⌨️ Task 3 – User Input

### Script: `greet.sh`

```bash
#!/bin/bash

read -p "Enter your name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"
```

### Example Output

```
Enter your name: Divyat
Enter your favourite tool: Docker
Hello Divyat, your favourite tool is Docker
```

---

## 🔀 Task 4 – If-Else Conditions

### Script 1: `check_number.sh`

```bash
#!/bin/bash

read -p "Enter a number: " NUM

if [ $NUM -gt 0 ]; then
    echo "The number is positive"
elif [ $NUM -lt 0 ]; then
    echo "The number is negative"
else
    echo "The number is zero"
fi
```

### Script 2: `file_check.sh`

```bash
#!/bin/bash

read -p "Enter filename: " FILE

if [ -f "$FILE" ]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

---

## 🧩 Task 5 – Combined Script

### Script: `server_check.sh`

```bash
#!/bin/bash

SERVICE="nginx"

read -p "Do you want to check the status of $SERVICE? (y/n): " ANSWER

if [ "$ANSWER" = "y" ]; then
    STATUS=$(systemctl is-active $SERVICE)
    echo "Service status: $STATUS"
else
    echo "Skipped."
fi
```

### Example Output

```
Do you want to check the status of nginx? (y/n): y
Service status: active
```

---

## 🎯 Key Learnings

1. `#!/bin/bash` (shebang) tells Linux which interpreter should run the script
2. Variables store data and are accessed using `$VARIABLE_NAME`
3. `read` allows user interaction in scripts
4. `if-else` statements help scripts make decisions
5. Shell scripts are powerful for automating DevOps tasks

---

## 📁 Folder Structure for Submission

```
2026/day-16/
│── hello.sh
│── variables.sh
│── greet.sh
│── check_number.sh
│── file_check.sh
│── server_check.sh
│── day-16-shell-scripting.md
```
