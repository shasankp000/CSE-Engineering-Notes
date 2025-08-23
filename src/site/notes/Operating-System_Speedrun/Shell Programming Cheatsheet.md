---
{"dg-publish":true,"permalink":"/operating-system-speedrun/shell-programming-cheatsheet/","title":"Linux shell programming Cheatsheet -- Operating Systems","tags":["Semester-5","Linux"],"created":"2025-03-06T18:33:28.757+05:30"}
---

---
# Basic stuff

```bash
#!/bin/zsh
# Above line tells the system which shell to run the program in.
# This is a comment.

echo "Hello! I am simple zsh program!" #This is the print statement.
echo "May I know your name?"
read name # Takes a user input in the variable name.
echo "Hello $name! It is nice to meet you!" # Can invoke the variable using $<var> even within a string, similar to an f-string in python.
echo "May I know your age?"
read age
# Ensure spaces between [ and $age, and before the closing ]
if [ $age -gt 18 ] # opening if statement with the operator -gt which stands for "greater than".
then
    echo "You are an adult $name! How is life treating you?"
else
    echo "You are not an adult $name, yet. Enjoy the ride while it lasts!"
fi # end if block


# For numeric comparison stuff like -gt -lt -leq -geq -eq is used.
# For string comparison (lexicographically), < > are used
```

# Loops

```bash
#!/bin/zsh

for i in 1 2 3 4 5 # declare for condition
do # what to execute in the loop
    echo "Current number in the loop is: $i"
done # end of the do block


j=0

while [ $j -le 5 ] ; do
    echo "$j"
    ((j++))
  # commands to execute repeatedly
done
```

Here we didn't do

```bash
$j++
```

Since the dollar sign before j causes it to be treated as a variable substitution, rather than an increment operation.

# Functions

Just write

```bash
function_name() {

  pos1=$1
  pos2=$2 #...and so on

  # <your code goes here>

}

function_name arg1 arg2 .... #function gets called here
```

# grep and sed

`grep`
The `grep` command is used to search for patterns within files. It stands for "Global Regular Expression Print."

Basic Usage: grep [options] pattern [file...]
Options:

```bash
-q: Quiet mode. grep will not output anything but will return an exit status indicating whether a match was found.
-i: Case-insensitive search.
-v: Invert the match. Shows lines that do not match the pattern.
-r or -R: Recursively search through directories.
-l: Print only the names of files with matching lines.
```



The `sed` command is a stream editor used to perform basic text transformations on an input stream (a file or input from a pipeline).

```shell
Basic Usage: sed [options] 'command' [file...]
Common Commands:
s/pattern/replacement/: Substitutes occurrences of pattern with replacement. For example, sed 's/UNIX/Linux/g' file.txt replaces all occurrences of "UNIX" with "Linux" in file.txt.
d: Deletes lines matching a pattern. For example, sed '/pattern/d' file.txt deletes lines containing "pattern".
p: Prints lines matching a pattern.
```

# CLI arguments

```bash
if [ $# -ne 3 ]; then:
```
```
#: This symbol starts a comment in shell scripts.
if: Begins the conditional statement.
[ $# -ne 3 ]: Checks if the number of command-line arguments ($#) is not equal to (-ne) 3.
$# is a special variable that holds the number of positional parameters (i.e., command-line arguments) passed to the script.
-ne stands for "not equal."
The condition [ $# -ne 3 ] evaluates to true if the number of arguments is not 3.
```


# Logical Operators

In shell scripting, logical operators are used to perform boolean operations (like AND, OR, and NOT) for condition evaluation. The following are the main logical operators used in shell scripting:

### 1. **AND Operator**
   - **Symbol**: `&&`
   - **Usage**: Both conditions must be true for the entire expression to evaluate to true.
   - **Example**:
     ```bash
     if [[ $a -gt 10 && $b -lt 20 ]]; then
         echo "Both conditions are true"
     fi
     ```

### 2. **OR Operator**
   - **Symbol**: `||`
   - **Usage**: At least one of the conditions must be true for the entire expression to evaluate to true.
   - **Example**:
     ```bash
     if [[ $a -gt 10 || $b -lt 20 ]]; then
         echo "At least one condition is true"
     fi
     ```

### 3. **NOT Operator**
   - **Symbol**: `!`
   - **Usage**: Negates the value of a condition (true becomes false, and false becomes true).
   - **Example**:
     ```bash
     if [[ ! $a -gt 10 ]]; then
         echo "Condition is false"
     fi
     ```

### 4. **Combining Conditions**
   - You can combine multiple conditions using parentheses `()` and logical operators.
   - **Example**:
     ```bash
     if [[ ( $a -gt 10 && $b -lt 20 ) || $c -eq 5 ]]; then
         echo "Combined condition is true"
     fi
     ```

### 5. **Conditional Operators for Integers**
   You often see integer comparisons combined with logical operators, such as:
   - `-eq`: Equal to
   - `-ne`: Not equal to
   - `-gt`: Greater than
   - `-lt`: Less than
   - `-ge`: Greater than or equal to
   - `-le`: Less than or equal to

   **Example**:
   ```bash
   if [[ $a -ge 10 && $b -le 5 ]]; then
       echo "Both conditions are true"
   fi
   ```

### 6. **Conditional Operators for Strings**
   String comparison can also be combined with logical operators:
   - `=` or `==`: String equality
   - `!=`: String inequality
   - `-z`: True if the string is null (empty)
   - `-n`: True if the string is not null (not empty)

   **Example**:
   ```bash
   if [[ $str1 == "hello" && -n $str2 ]]; then
       echo "Both conditions are true"
   fi
   ```

### Summary of Common Logical Operators:

| Operator | Description                             | Example Usage                                    |
|----------|-----------------------------------------|-------------------------------------------------|
| `&&`     | Logical AND                             | `[[ $a -gt 10 && $b -lt 20 ]]`                  |
| `||`     | Logical OR                              | `[[ $a -gt 10 || $b -lt 20 ]]`                  |
| `!`      | Logical NOT                             | `[[ ! $a -gt 10 ]]`                             |
| `-eq`    | Integer equality                        | `[[ $a -eq $b ]]`                               |
| `-ne`    | Integer inequality                      | `[[ $a -ne $b ]]`                               |
| `-gt`    | Greater than (integers)                 | `[[ $a -gt 10 ]]`                               |
| `-lt`    | Less than (integers)                    | `[[ $a -lt 10 ]]`                               |
| `-ge`    | Greater than or equal to (integers)     | `[[ $a -ge 10 ]]`                               |
| `-le`    | Less than or equal to (integers)        | `[[ $a -le 10 ]]`                               |
| `==`     | String equality                         | `[[ $str1 == "hello" ]]`                        |
| `!=`     | String inequality                       | `[[ $str1 != "world" ]]`                        |
| `-n`     | String is not null (not empty)          | `[[ -n $str ]]`                                 |
| `-z`     | String is null (empty)                  | `[[ -z $str ]]`                                 |

These logical operators are used in `if`, `while`, `until`, and `test` conditions to control the flow of shell scripts.
