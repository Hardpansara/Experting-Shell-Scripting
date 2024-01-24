# Experting-Shell-Scripting

## Shell Scripting Finale: Functions and Advanced Gems 

Developers, welcome to the concluding act of our shell scripting adventure! Today, we unravel the power of functions, explore advanced examples, and gracefully bid farewell to this journey. Let's craft a script finale with precision and professionalism.

### Unleashing the Power of Functions ✨

In shell scripting, functions are reusable code blocks that perform specific tasks. They modularize your script, making it more readable, maintainable, and easier to manage. Define functions using the `function` keyword or simply by providing the function name followed by parentheses.

### Function! 

**Hello, World!** 

```bash
#!/bin/bash

Hello () {
  echo "Hello, World!"
}

Hello
```

This code defines a `Hello` function that prints "Hello, World!" using the `echo` command. We then call the function to execute it.

**Parameterized Function** 

```bash
#!/bin/bash

Hello () {
  echo "Hello, $1 $2"
}

Hello Hard Pansara
```

Here, we create a `Hello` function that accepts two parameters (`$1` and `$2`). When we call `Hello Hard Pansara`, it outputs "Hello, Hard Pansara".

**Return Function!** 

```bash
#!/bin/bash

Hello () {
  echo "Hello, $1 $2"
  return 20
}

Hello Hard Pansara!

ret=$?

echo "Return value is $ret"
```

This `Hello` function returns a value using `return`. We call it with "Hard Pansara!", store the return value in `ret`, and print it using `echo`.

**Dynamic Greeting Generator: Time for Magic!** 

```bash
function greeting {
  current_hour=$(date +"%H")

  if [ $current_hour -lt 12 ]; then
    echo "Good morning!"
  elif [ $current_hour -lt 18 ]; then
    echo "Good afternoon!"
  else
    echo "Good evening!"
  fi
}

greeting
```

This `greeting` function uses the current hour (`date +"%H"`) to generate a personalized greeting using conditionals.

### Shell Scripting Gems: Illuminate with Brilliance! 

**Automated System Report: Unveiling Insights!** 

```bash
#!/bin/bash

echo "System Report: $(date)"
echo "---------------------"

# Display system information
uname -a

# Display disk space usage
df -h

# Display memory usage
free -h
```

This Bash script generates a system report upon execution. It includes:

- **System Report Header:** Prints the current date and time.
- **Separator Line:** Visually separates sections.
- **System Information:** Uses `uname -a` to display details like kernel version and machine type.
- **Disk Space Usage:** Uses `df -h` to show disk space usage in a human-readable format.
- **Memory Usage:** Uses `free -h` to display memory usage information.

This script provides a quick overview of key system details at a glance.

**Directory Cleanup Wizard: Streamline Your Space with Expert Precision!** 

```bash
#!/bin/bash

echo "Cleaning up the directory: $(pwd)"
echo "----------------------------------"

# Remove log files older than 7 days
find . -name "*.log" -mtime +7 -exec rm {} \;

echo "Cleanup complete!"
```

This script cleans up the current directory by removing log files older than 7 days:

- **Cleanup Header:** Indicates the directory being cleaned and uses `$(pwd)` to dynamically print the path.
- **Separator Line:** Visually separates the header from the cleanup details.
- **Remove Log Files:** Uses `find` to search for log files older than 7 days (`-mtime +7`) and removes them using `rm`.
- **Cleanup Completion Message:** Confirms the successful cleanup.

This script streamlines routine maintenance, ensuring the removal of redundant files and maintaining optimal organization within your directories.
