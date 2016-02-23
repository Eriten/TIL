# Subshells

Today I was trying to execute the following code. Can you guess what the result is?
```
cat file |
while IFS= read -r line
do
    return_code=0
done
echo ${return_code}
```

You would think that the output is 0, right? The answer is no. It will not print any charactor. After researching a little bit, I realized that when calling while in Bash/Shell, it is running in a subshell where it has its own set of variables other than the global variables.

There seems to be [many workarounds to solve this problem](http://mywiki.wooledge.org/BashFAQ/024), but I've found the following the most elegant among the all listed in the link. This solution ensures that the while and echo execute in the same subshell. You can perform such hack by having a curly braces or parathesis block around the code.

```
cat file |
{
  while IFS= read -r line
  do
      return_code=0
  done
  echo ${return_code}
}
```

Subshells can also happen in the following scenarios -
- Executing other programs
- Piping in bash
- Background commands ( `foo=bar &` )
- Variable expansion ( `"$(ls)"`)
- Process Substitution ( `true < <(foo=bar)` )


Reference: http://www.vidarholen.net/contents/blog/?p=178
