
### Named Pipe
```
while IFS= read -r -d $'\0' file; do
  dosomethingwith "$file"        # do something with each file
done < <(find /bar -name *foo* -print0)
```
Kinds of equal to
```
find /bar -name *foo* -print0 | while IFS= read -r -d $'\0' file; do
  dosomethingwith "$file"        # do something with each file
done
```


### Array
```
"$array[@]"
```