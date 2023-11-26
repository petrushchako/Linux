### SED
```
echo "some text" > test1.txt

sed -i "s/some/Some/" test1.txt #This fails
sed -i .bak "s/some/Some/" test1.txt #Works
```


#### Workaround:
```
brew isntall gnu-sed
gsed -i "s/some/Some/" test1.txt
```

#### Alternative workaround:

Instead of calling sed with **sed**, I do **./bin/sed**
And this is the wrappet script in my **~/project/bin/sed**
```
#!.bin/bash
if [[ "$OSTYPE" == "darwin"* ]]; then
    exec "gsed" "$@"
else
    exec "sed" "$@"
fi
```

Don't forget to **chmod 755** the wrapper script.