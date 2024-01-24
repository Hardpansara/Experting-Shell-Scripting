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

**Example**

```bash
#!/bin/bash

# 1. Function to take input from the user
getInput() {
  read -p "Enter a string to check for palindrome: " inputString
  echo "$inputString"
}

# 2. Function to check if a string is a palindrome
checkPalindrome() {
  inputString="$1"
  reversedString=""

  # Reverse the input string
  for (( i = $((${#inputString} - 1)); i >= 0; i-- )); do
    reversedString+=${inputString:$i:1}
  done

  # Compare the input string with its reversed version
  if [[ "$inputString" == "$reversedString" ]]; then
    echo "$inputString is a palindrome."
  else
    echo "$inputString is not a palindrome."
  fi
}

# Main program
inputString=$(getInput)
checkPalindrome "$inputString"

```
Function `gerInput()` :
- Prompts the user to enter a string using `read -p`.
- Stores the entered string in the `inputString` variable.
- Echoes the string back to the user for confirmation.

Function `checkPalindrome()` :
- Takes the input string as an argument (`"$1"`).
- Initializes an empty string `reversedString` to store the reversed version.
- Iterates through the input string in reverse order using a `for` loop.
- Appends each character to the `reversedString`.
- Compares the `inputString` with the `reversedString` using a conditional statement.
- Prints whether the string is a palindrome or not.

Main program :
- Calls the `getInput()` function to get the input from the user and stores it in the `inputString` variable.
- Passes the `inputString` to the `checkPalindrome()` function to check for palindrome.

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

**Network Information**
```bash
#!/bin/bash

echo "Network Information:"
echo "--------------------"

# Display hostname
hostname

# Display IP address
ip addr show

# Display network interfaces
ip link show

# Display routing table
ip route
```
- **Hostname Display**:`hostname` Runs the hostname command to retrieve and print the system's hostname, which is its unique identifier on the network.
- **Network Interfaces Display**:`ip link show`: Runs the `ip link show` command to list all available network interfaces (e.g., Ethernet, Wi-Fi) and their current status (up/down). This can be helpful for troubleshooting network connectivity issues.
- **Routing Table Display**:`ip route`: Runs the `ip route` command to show the system's routing table, which specifies how it directs network traffic to different destinations. This can be useful for understanding how your machine reaches various network resources and optimizing routing paths.

**CPU Usage Monitor**
```bash
#!/bin/bash

echo "CPU Usage Monitor:"
echo "-------------------"

while true; do
  top -bn1 | head -n 15
  sleep 5
done
```

- `while true; do`: Initiates an infinite loop.
- `top -bn1 | head -n 15`: Executes the top command to display system resource usage. The options -bn1 specify a single iteration in non-interactive mode. The output is then piped (|) to head -n 15, which limits the output to the first 15 lines, showing the top processes.
- `sleep 5`: Pauses the script for 5 seconds before the next iteration of the loop.
- `done:` Marks the end of the while loop.

