# 🚀 Day 17 – Shell Scripting: Loops, Arguments & Error Handling

Today I leveled up my Bash scripting skills by learning:

- ✅ For loops  
- ✅ While loops  
- ✅ Command-line arguments  
- ✅ Installing packages via script  
- ✅ Basic error handling  

This is where shell scripting starts feeling powerful 💪

Let’s break everything down in **very simple language** so even a beginner can understand.

---

# 🧠 What I Learned Today

1. Loops help automate repetitive tasks.
2. Arguments make scripts dynamic.
3. Error handling makes scripts production-ready.

---

# 🔁 Task 1 – For Loop

A **for loop** runs code multiple times.

Think of it like:

> “Do this task for every item in this list.”

---

## 📝 Script 1: `for_loop.sh`

```bash
#!/bin/bash

for fruit in apple mango banana orange grapes
do
    echo "Fruit: $fruit"
done
```

### 🔍 Explanation (Line by Line)

- `#!/bin/bash` → Tells Linux this is a bash script.
- `for fruit in ...` → Loop through each item.
- `fruit` → Variable holding current value.
- `do` → Start of loop block.
- `echo` → Print text.
- `done` → End of loop.

### ▶ Output

```
Fruit: apple
Fruit: mango
Fruit: banana
Fruit: orange
Fruit: grapes
```

---

## 📝 Script 2: `count.sh`

Print numbers from 1 to 10.

```bash
#!/bin/bash

for i in {1..10}
do
    echo "Number: $i"
done
```

### 💡 Explanation

- `{1..10}` → Bash range.
- `$i` → Current number.

### ▶ Output

```
Number: 1
Number: 2
...
Number: 10
```

---

# 🔄 Task 2 – While Loop

A **while loop** runs as long as a condition is TRUE.

Think:

> “Keep doing this while something is true.”

---

## 📝 Script: `countdown.sh`

```bash
#!/bin/bash

read -p "Enter a number: " num

while [ $num -ge 0 ]
do
    echo $num
    num=$((num - 1))
done

echo "Done!"
```

### 🔍 Explanation

- `read -p` → Takes input from user.
- `while [ condition ]` → Loop condition.
- `-ge` → Greater than or equal.
- `$(( ))` → Arithmetic operation.

### ▶ Example Run

```
Enter a number: 5
5
4
3
2
1
0
Done!
```

---

# 🧾 Task 3 – Command-Line Arguments

Arguments make scripts flexible.

When you run:

```
./script.sh hello world
```

- `$1` → hello  
- `$2` → world  
- `$#` → total arguments  
- `$@` → all arguments  
- `$0` → script name  

---

## 📝 Script: `greet.sh`

```bash
#!/bin/bash

if [ -z "$1" ]
then
    echo "Usage: ./greet.sh <name>"
else
    echo "Hello, $1!"
fi
```

### ▶ Example

```
./greet.sh Divyat
Hello, Divyat!
```

If no argument:

```
Usage: ./greet.sh <name>
```

---

## 📝 Script: `args_demo.sh`

```bash
#!/bin/bash

echo "Script name: $0"
echo "Total arguments: $#"
echo "All arguments: $@"
```

### ▶ Example

```
./args_demo.sh apple mango
```

Output:

```
Script name: ./args_demo.sh
Total arguments: 2
All arguments: apple mango
```

---

# 📦 Task 4 – Install Packages via Script

Now we automate package installation.

This is **real DevOps scripting** 🔥

---

## 📝 Script: `install_packages.sh`

```bash
#!/bin/bash

# Check if running as root
if [ "$EUID" -ne 0 ]
then
    echo "Please run as root!"
    exit 1
fi

packages=("nginx" "curl" "wget")

for pkg in "${packages[@]}"
do
    if dpkg -s "$pkg" &> /dev/null
    then
        echo "$pkg is already installed."
    else
        echo "Installing $pkg..."
        apt install -y "$pkg"
    fi
done
```

### ▶ Run Script

```
sudo ./install_packages.sh
```

---

# 🛑 Task 5 – Error Handling

Professional scripts must handle errors.

---

## 📝 Script: `safe_script.sh`

```bash
#!/bin/bash

set -e

mkdir -p /tmp/devops-test

cd /tmp/devops-test

touch testfile.txt

echo "Script completed!"
```

### 🔍 Explanation

- `set -e` → Exit script immediately if any command fails.
- `mkdir -p` → Create directory if not exists.
- `||` → Runs right command if left fails (used in alternate version).

---

# 📁 Final Project Structure

```
2026/day-17/
│
├── for_loop.sh
├── count.sh
├── countdown.sh
├── greet.sh
├── args_demo.sh
├── install_packages.sh
├── safe_script.sh
└── day-17-scripting.md
```

---

# 🔥 Real DevOps Takeaways

1. Loops save time.
2. Arguments make scripts reusable.
3. Root checks prevent permission issues.
4. Error handling makes scripts production-safe.
5. Automation is everything in DevOps.

---

# 🏁 How I Ran Everything

```bash
chmod +x scriptname.sh
./scriptname.sh
```

For root scripts:

```bash
sudo ./install_packages.sh
```

---

# 📢 Learning in Public

Today I automated:

- Fruit listing 🍎  
- Countdown ⏳  
- Greeting users 👋  
- Installing packages 📦  
- Error handling ⚠  

Feeling more confident with Bash now 💪  

Consistency > Motivation.

See you on Day 18 🚀

