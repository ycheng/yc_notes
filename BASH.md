* For loop
```
for i in {0..10..2}
do 
  echo "Welcome $i times"
done

for i in $(seq 1 2 20)
do
   echo "Welcome $i times"
done
```

* If
```
  if [ -d $d ]
  then
    echo "create link for" $d
    ln -s $d .
  fi
```
