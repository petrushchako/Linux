# Here Document `<<EOF`

A Here Document allows you to feed multi-line input directly into a command from within a shell script or terminal. This is commonly used to write configuration files, script templates, or even embedded documentation.


## Basic Syntax
```bash
command <<EOF
multi-line content
goes here
EOF
```
The `EOF` is just a marker — you can replace it with any other word, but `EOF` is the most common.

## Writing Multi-Line Text to a File
### Example
- Write/overrite:
     ```bash
    cat <<EOF > myfile.txt
    This is a multi-line text block.
    It will be saved into myfile.txt.
    EOF
    ```
- Append:
   ```bash
    cat <<EOF >> myfile.txt
    This is a multi-line text block.
    It will be saved into myfile.txt.
    EOF
    ```
### Result in `myfile.txt`
```
This is a multi-line text block.
It will be saved into myfile.txt.
```

## Using Variables Inside Here Document
### Example
```bash
USERNAME="cloudguru"
SERVER="prod-server"

cat <<EOF > config.txt
User: $USERNAME
Server: $SERVER
Welcome $USERNAME, you are connected to $SERVER.
EOF
```

### Result in `config.txt`
```
User: cloudguru
Server: prod-server
Welcome cloudguru, you are connected to prod-server.
```
In this case, **variables are expanded (interpreted)** because we used an **unquoted `EOF`**.

## Preventing Variable Expansion
If you want to **preserve variables as plain text** (for example, to show in documentation or templates), **quote the marker** like this:

### Example
```bash
cat <<'EOF' > literal.txt
User: $USERNAME
Server: $SERVER
This will not expand variables.
EOF
```

### Result in `literal.txt`
```
User: $USERNAME
Server: $SERVER
This will not expand variables.
```
