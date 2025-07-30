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
