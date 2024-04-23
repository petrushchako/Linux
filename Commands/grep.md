# `grep`

## Description:
`grep` is a command-line utility used for searching text patterns in files. It allows users to specify a pattern to match, and it will output lines in those files that contain the specified pattern.

## Syntax:
`grep [options] pattern [file...]`


## Options:
- `-i, --ignore-case`: Ignore case distinctions in both the pattern and input files.
- `-v, --invert-match`: Invert the sense of matching, displaying lines that do not contain the pattern.
- `-r, --recursive`: Recursively search subdirectories.
- `-n, --line-number`: Prefix each line of output with the 1-based line number within its input file.
- `-l, --files-with-matches`: Print only the names of files containing the pattern.
- `-c, --count`: Suppress normal output; instead, print a count of matching lines for each input file.
- `-e pattern, --regexp=pattern`: Specify a pattern to search for.
- `-E, --extended-regexp`: Interpret pattern as an extended regular expression.
- `-w, --word-regexp`: Match only whole words.
- `-A NUM, --after-context=NUM`: Print NUM lines of trailing context after matching lines.
- `-B NUM, --before-context=NUM`: Print NUM lines of leading context before matching lines.

