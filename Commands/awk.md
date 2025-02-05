# `awk`

## Overview

AWK is a powerful text-processing command in Unix/Linux used for pattern scanning and processing. It is particularly useful for extracting and manipulating data from structured text files.

### Quick Example
Suppose we have a file `employees.txt` with the following content:
```
Alice 30 Developer
Bob 25 Designer
Charlie 35 Manager
```
To print only the names and job titles, we can use:
```bash
awk '{print $1, $3}' employees.txt
```
**Output:**
```
Alice Developer
Bob Designer
Charlie Manager
```
This demonstrates how AWK can efficiently extract and format structured data.

AWK is a powerful text-processing command in Unix/Linux used for pattern scanning and processing. It is particularly useful for extracting and manipulating data from structured text files.

## Syntax

```bash
awk 'pattern { action }' file
```

- `pattern` → Specifies when the action should be executed.
- `action` → Specifies what to do when the pattern matches.
- `file` → Input file to process.

<br><br><br>

## Common Usage
### 1. Print Specific Columns
Suppose we have a file named `file.txt` with the following content:

```
John 28 Engineer
Alice 30 Designer
Bob 25 Developer
```

We can extract and display specific columns, such as the first and third columns:
```bash
awk '{print $1, $3}' file.txt
```

**Output:**
```
John Engineer
Alice Designer
Bob Developer
```

This prints the first and third columns from `file.txt`, showing names and job roles.

<br>

### 2. Filter Lines Matching a Pattern
Print lines containing a specific word:
```bash
awk '/error/ {print}' logfile.txt
```
This prints all lines in `logfile.txt` that contain the word "error".

<br>

### 3. Using Field Separator (FS)
If fields are separated by a delimiter like a comma (CSV file):
```bash
awk -F, '{print $2}' data.csv
```
This prints the second column from a comma-separated file.

<br>

### 4. Print Lines Based on a Condition
Suppose we have a file named `data.txt` with the following content:
```
Alice 25 120
Bob 30 90
Charlie 28 150
David 35 80
```
We can use AWK to print the first and third columns where the third column value is greater than 100:
```bash
awk '$3 > 100 {print $1, $3}' data.txt
```
**Output:**
```
Alice 120
Charlie 150
```

<br>

### 5. Count Lines in a File
```bash
awk 'END {print NR}' file.txt
```
This prints the total number of lines in `file.txt`.


<br>

### 6. Perform Arithmetic Operations
Suppose we have a file named `sales.txt` with the following content:
```
John 200
Alice 350
Bob 150
```
We can use AWK to sum up the values in the second column:
```bash
awk '{sum+=$2} END {print "Total:", sum}' sales.txt
```
**Output:**
```
Total: 700
```

<br>

## Conclusion
AWK is a versatile tool for text processing, making it invaluable for filtering, extracting, and manipulating data in Unix/Linux environments. Mastering its syntax and options can significantly improve data handling efficiency.
In addition to the examples above, AWK supports built-in functions for string manipulation, mathematical operations, and date formatting. It also allows multi-line processing and the ability to write complex AWK scripts for automation.
