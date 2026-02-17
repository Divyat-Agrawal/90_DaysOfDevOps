# 🚀 Day 18 – Shell Scripting: Functions & Strict Mode 


Today I learned how to write **clean, reusable, and safe Bash scripts** like a real DevOps engineer.

Before today, I was writing simple scripts.  
Today, I started writing **structured and production-ready scripts**.

---

# 🧠 What I Learned Today

- ✅ Functions in Bash  
- ✅ Passing arguments to functions  
- ✅ Arithmetic inside functions  
- ✅ Local variables  
- ✅ Strict mode (`set -euo pipefail`)  
- ✅ Building a real system info script  

---

# 🔹 Task 1 – Basic Functions

## 📝 `functions.sh`

```bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

add() {
    sum=$(( $1 + $2 ))
    echo "Sum is: $sum"
}

greet "Divyat"
add 5 10
```

---

## 🔍 Explanation

### `greet()`
- Defines a function.
- `$1` = first argument passed.
- `greet "Divyat"` → prints `Hello, Divyat!`

### `add()`
- Takes two numbers.
- `$(( ))` is used for arithmetic.
- `$1` and `$2` are the two numbers.

### ▶ Output

```
Hello, Divyat!
Sum is: 15
```

---

# 🔹 Task 2 – Disk & Memory Check Using Functions

## 📝 `disk_check.sh`

```bash
#!/bin/bash

check_disk() {
    echo "Disk Usage:"
    df -h /
}

check_memory() {
    echo "Memory Usage:"
    free -h
}

check_disk
echo "-------------------"
check_memory
```

---

## 🔍 Explanation

- `df -h /` → Shows disk usage of root partition.
- `free -h` → Shows memory usage.
- Functions help organize system checks cleanly.

---

# 🔥 Task 3 – Strict Mode (`set -euo pipefail`)

## 📝 `strict_demo.sh`

```bash
#!/bin/bash
set -euo pipefail

echo $UNDEFINED_VAR

echo "This line will not run"
```

---

## 🔍 What Each Flag Does

### `set -e`
- Exit immediately if any command fails.

### `set -u`
- Exit if using an undefined variable.

### `set -o pipefail`
- If any command in a pipeline fails, whole pipeline fails.

---

## 🧠 Why Strict Mode Is Important

Without strict mode:
- Scripts continue even after errors.
- Bugs stay hidden.

With strict mode:
- Errors stop execution.
- Scripts become safe and predictable.

---

# 🔹 Task 4 – Local Variables

## 📝 `local_demo.sh`

```bash
#!/bin/bash

var="Global"

show_local() {
    local var="Local"
    echo "Inside function: $var"
}

show_local
echo "Outside function: $var"
```

---

## 🔍 Explanation

- `local var="Local"` → Variable exists only inside function.
- Outside function → Global variable remains unchanged.

### ▶ Output

```
Inside function: Local
Outside function: Global
```

---

# 🔥 Task 5 – System Info Reporter Script

## 📝 `system_info.sh`

```bash
#!/bin/bash
set -euo pipefail

print_header() {
    echo "==============================="
    echo "$1"
    echo "==============================="
}

hostname_info() {
    print_header "Hostname & OS Info"
    hostname
    uname -a
}

uptime_info() {
    print_header "System Uptime"
    uptime
}

memory_info() {
    print_header "Memory Usage"
    free -h
}

cpu_info() {
    print_header "Top 5 CPU Processes"
    ps -eo pid,cmd,%cpu --sort=-%cpu | head -6
}

main() {
    hostname_info
    uptime_info
    memory_info
    cpu_info
}

main
```

---

# 🔍 Explanation

- `hostname` → Shows system name.
- `uname -a` → Shows OS information.
- `uptime` → Shows how long system has been running.
- `free -h` → Memory usage.
- `ps` → Lists running processes.
- `head -6` → Shows top 5 processes (plus header).

---

# 📁 Folder Structure

```
2026/day-18/
│
├── functions.sh
├── disk_check.sh
├── strict_demo.sh
├── local_demo.sh
├── system_info.sh
└── day-18-scripting.md
```

---

# 🏁 How to Run Scripts

```bash
chmod +x script.sh
./script.sh
```

---

# 🚀 Key Takeaways

1. Functions make scripts reusable.
2. `local` prevents variable conflicts.
3. `set -euo pipefail` makes scripts safe.
4. Clean structure improves readability.
5. Real DevOps scripts use strict mode.

