# matriochka


Ok first let's downoad the file !


now you have the file we can start by see what is inside !
```bash
cat matriochka
```

we can see that there is some random strings in here, but if we tae a closer look we can see that is base64 encoded !

so let's go decode it 

```bash
cat matriochka | base64 -d
```

we see that it a look of a zip archive ok let's go 


```bash
cat matriochka | base64 -d >> matriochka.zip
```

then we can unzip it !

```bash
unzip matriochka.zip
```

ok we have an ohter txt file...

you see the thing come, let's be smart and do automaticly the things !


```bash
#!/bin/bash

filename=$1
rm -rf tmp
mkdir tmp
cp $1 tmp/$1.txt
cd tmp
for i in {1..100}
do
        cat $1.txt | base64 -d >> $1.zip
        rm $1.txt
        unzip -o $1.zip
        rm $1.zip
done
cat $1.txt

```

i just give you the all script have fun !!
