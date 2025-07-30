# `base64`

The `base64` command allows you to encode and decode files or strings using the Base64 encoding scheme, which is commonly used to safely transmit binary data as text.



## Encoding
### Encode a File to Base64
```bash
base64 input.txt > encoded.txt
````
This reads `input.txt` and writes the Base64-encoded content to `encoded.txt`.

### Print Base64 Output to Terminal
```bash
base64 input.txt
```

This displays the encoded content directly in the terminal.

### Encode a String
```bash
echo -n "Hello World" | base64
```

**Output:**

```
SGVsbG8gV29ybGQ=
```

> `-n` prevents `echo` from appending a newline.

<br><br><br>

## Decoding
### Decode a Base64 File
```bash
base64 -d encoded.txt > decoded.txt
```

> On **macOS**, use `-D` instead of `-d` if needed:

```bash
base64 -D encoded.txt > decoded.txt
```

This restores the original content and saves it to `decoded.txt`.

### Decode a Base64 String

```bash
echo "SGVsbG8gV29ybGQ=" | base64 -d
```

> macOS alternative:

```bash
echo "SGVsbG8gV29ybGQ=" | base64 -D
```

**Output:**

```
Hello World
```

<br><br><br>

## Notes
* The `base64` tool is included by default on most Unix-like systems.
* Use `-w 0` (Linux only) to avoid line wrapping during encoding:

```bash
base64 -w 0 input.txt
```

## Summary

| Task            | Command Example                      |
| --------------- | ------------------------------------ |
| Encode a file   | `base64 input.txt > encoded.txt`     |
| Decode a file   | `base64 -d encoded.txt > output.txt` |
| Encode a string | `echo -n "text" \| base64`           |
| Decode a string | `echo "encoded" \| base64 -d`        |
