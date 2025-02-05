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


For more advanced features, consider learning AWK scripting.

