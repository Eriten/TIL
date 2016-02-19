# Read Command Output Line by Line

We can use stdbuf to buffer the output and outputs them line by line as shown
as follows -

```
stdbuf -oeL command |
  while IFS= read -r line
  do
    echo "$line" # Output line

    # Output ERRRORRRRRRRRRR if the line contains Error
    if [[ "$line" == *"Error"* ]]
    then
        echo "ERRORRRRRRRRRRRRRR"
    fi
  done
```

* Option o of stdbuf buffers stdout and Option e buffers stderr
* Option L says the stream will be line buffered
* stdbuf is available on GNU and FreeBSD systems

Reference: http://unix.stackexchange.com/questions/117501/in-bash-script-how-to-capture-stdout-line-by-line 


