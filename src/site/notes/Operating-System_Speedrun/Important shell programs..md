---
{"dg-publish":true,"permalink":"/operating-system-speedrun/important-shell-programs/","title":"Important Shell Programs -- Operating Systems","tags":["Semester-5","Linux"],"created":"2025-03-06T18:33:28.686+05:30"}
---


---

# 1. Get file details using `stat`

```bash
#!/bin/zsh

# The stat command will be used here to provide the details of the file.

# Check if exactly one argument is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 filename"
    exit 1
fi

# Store the argument in a variable
file=$1 # the first positional argument.

# Check if the file exists
if [ -f "$file" ]; then
    # Display the last modified time of the file
    echo "Last modified time of $file:"
    stat -c %y "$file" # Uses the stat command with the -c %y option to display the last modification time of the file. The %y format specifier shows the last modification time in a human-readable format.
else
    # Display a message if the file does not exist
    echo "File $file does not exist."
    exit 1
fi

```
---
# 2.  Open file and modify file contents using `grep` and `sed`

```bash
#!/bin/zsh


# Check if exactly one argument is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 filename"
    exit 1
fi

# Store the argument in a variable
file=$1


# Check if the file exists
if [ -f "$file" ]; then
    # Check if the file contains the word "UNIX"
    #grep -q "UNIX" "$file" checks if the word "UNIX" is present in the file.
    #-q makes grep operate quietly without printing matching lines (just return the exit status).
    if grep -q "UNIX" "$file"; then
        # Remove the word "UNIX" from the file and save the changes
        sed -i 's/UNIX//g' "$file"
        # sed -i 's/UNIX//g' "$file" uses sed to remove all occurrences of the word "UNIX" from the file.
        #-i option edits the file in place.
        #s/UNIX//g specifies the substitution command to replace "UNIX" with nothing (//), and g applies the replacement globally on each line.
        echo "The word 'UNIX' has been removed from $file."
    else
        echo "The word 'UNIX' was not found in $file."
    fi
else
    # Display a message if the file does not exist
    echo "File $file does not exist."
    exit 1
fi

```
---

# 3. Fibonacci

```bash
#!/bin/zsh

fibonacci() {
    places=$1

    current=0
    next=1

    echo "The Fibonacci series till $places places is: "

    echo -n "$current "

    for ((i=1; i<places; i++))  # Changed condition to 'i<places'
    do
        temp=$current # predecessor

        current=$((current + next))  # predecessor + next.
        next=$temp

        echo -n "$current "
    done

    echo # to print a newline after the output
}

fibonacci 20

```
---
# 4. Maximum of 3 numbers using CLI args

```bash
#!/bin/zsh

find_max_three() {
    num1=$1
    num2=$2
    num3=$3

    if [ $num1 -lt $num3 ] && [ $num2 -lt $num3 ]; then
        echo "$num3 is the maximum out of the three numbers!"
    elif [ $num1 -lt $num2 ] && [ $num2 -gt $num3 ]; then
        echo "$num2 is the maximum out of the three numbers!"
    elif [ $num1 -gt $num2 ] && [ $num1 -gt $num3 ]; then
        echo "$num1 is the maximum out of the three numbers!"
    else
        echo "There was an issue determining the maximum."
    fi
}

if [ $# -ne 3 ]
then
    echo "Usage: $0 num1 num2 num3"
    exit 1
fi

find_max_three $1 $2 $3
```
---

# 5. Factorial

```bash
#!/bin/zsh

factorial() {
    num=$1 # A positional argument for the factorial function.
    frac=1

    for ((i=num; i >= 1; i--))
    do
        frac=$((frac*i))
    done
    echo "Factorial of $num is $frac!"
}

echo -n "Enter a number to calculate its factorial: "
read num
factorial $num

```
---