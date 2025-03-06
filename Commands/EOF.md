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
