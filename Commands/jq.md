# `jq`

## Description:
`jq` is a lightweight and flexible command-line JSON processor. It allows users to parse, filter, and transform JSON data using simple expressions.

<br>

## Installation: 
### On Ubuntu/Debian:
```bash
sudo apt update
sudo apt install jq
```
### On macOS (with Homebrew):
```bash
brew install jq
```

<br>

## Basic Syntax:
```bash
jq [OPTIONS] FILTER [FILE]
```
- **FILTER**: A query expression that specifies how to process the JSON input.
- **FILE**: The JSON file to process. If omitted, `jq` reads from standard input.

<br>

## Options:

- `-c`: Output compact JSON instead of pretty-printed JSON.
- `-r`: Output raw strings (useful for extracting values without quotes).
- `-s`: Slurp mode (reads the entire input into an array instead of processing line by line).
- `-n`: Use `null` as input instead of reading from a file or standard input.
- `--arg NAME VALUE`: Pass a shell variable to `jq` as a JSON value.
- `--version`: Display the version of `jq`.

<br>

## Examples:

### 1. Pretty-Print JSON
Format JSON for better readability.
```bash
jq '.' file.json
```

### 2. Extract a Specific Key
Retrieve the value of a specific key.
```bash
jq '.keyName' file.json
```

### 3. Filter Based on a Condition
Retrieve JSON objects that satisfy a condition.
```bash
jq 'select(.keyName == "value")' file.json
```

### 4. Iterate Over an Array
Process each item in a JSON array.
```bash
jq '.arrayName[]' file.json
```

### 5. Modify JSON Data
Add or update a key-value pair.
```bash
jq '.keyName = "newValue"' file.json
```

### 6. Combine Keys
Combine values from multiple keys into a single output.
```bash
jq '.key1 + " " + .key2' file.json
```

### 7. Output Raw Strings
Print values without quotes.
```bash
jq -r '.keyName' file.json
```

### 8. Merge JSON Objects
Combine multiple JSON objects into one.
```bash
jq -s '.[0] * .[1]' file1.json file2.json
```

<br>

## Advanced Usage:

### Passing Variables
Pass shell variables into `jq`.
```bash
jq --arg varName "$shellVar" '.keyName = $varName' file.json
```

### Querying Nested Data
Access nested keys with a dot-separated path.
```bash
jq '.parentKey.childKey' file.json
```

### Using Built-in Functions
- `length`: Get the length of an array or string.
- `keys`: List all keys in an object.
- `has`: Check if a key exists.
```bash
jq 'keys' file.json
```

<br>

## Resources:
- Official Documentation: [https://stedolan.github.io/jq/manual/](https://stedolan.github.io/jq/manual/)
- Online JSON Formatter and Validator: [https://jsonformatter.org/](https://jsonformatter.org/)
