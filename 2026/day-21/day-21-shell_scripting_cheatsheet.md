# Shell Scripting Cheat Sheet

# Task 1: Basics

## Shebang

```bash
#!/bin/bash
```

Tells Linux which interpreter to use.

## Running a Script

```bash
chmod +x script.sh
./script.sh
bash script.sh
```

## Comments

```bash
# Single line comment
echo "Hello" # Inline comment
```

## Variables

```bash
NAME="DevOps"
echo $NAME
echo "$NAME"
echo '$NAME'
```

## User Input

```bash
read -p "Enter name: " NAME
echo $NAME
```

## Command-line Arguments

```bash
echo $0
echo $1
echo $#
echo $@
echo $?
```

---

# Task 2: Operators and Conditionals

## String Comparisons

```bash
[ "$a" = "$b" ]
[ "$a" != "$b" ]
[ -z "$a" ]
[ -n "$a" ]
```

## Integer Comparisons

```bash
[ $a -eq $b ]
[ $a -ne $b ]
[ $a -lt $b ]
[ $a -gt $b ]
```

## File Test Operators

```bash
[ -f file ]
[ -d dir ]
[ -r file ]
```

## if-else

```bash
if [ condition ]; then
    echo "Yes"
elif [ condition ]; then
    echo "Maybe"
else
    echo "No"
fi
```

## Logical Operators

```bash
[ condition ] && echo "True"
[ condition ] || echo "False"
! [ condition ]
```

## Case Statement

```bash
case $var in
    start) echo "Start";;
    stop) echo "Stop";;
    *) echo "Unknown";;
esac
```

---

# Task 3: Loops

## For Loop

```bash
for i in 1 2 3; do
    echo $i
done
```

## C-style For Loop

```bash
for ((i=0;i<5;i++)); do
    echo $i
done
```

## While Loop

```bash
while read line; do
    echo $line
done < file.txt
```

## Until Loop

```bash
until [ $a -gt 5 ]; do
    ((a++))
done
```

## Loop Control

```bash
break
continue
```

## Loop Files

```bash
for file in *.log; do
    echo $file
done
```

---

# Task 4: Functions

## Define and Call

```bash
greet() {
    echo "Hello"
}

greet
```

## Function Arguments

```bash
func() {
    echo $1
}

func "Hi"
```

## Return vs Echo

```bash
return 1
echo "data"
```

## Local Variables

```bash
func() {
    local var="test"
}
```

---

# Task 5: Text Processing Commands

## grep

```bash
grep -i "error" file
grep -r "text" .
grep -n "line" file
```

## awk

```bash
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
```

## sed

```bash
sed 's/old/new/g' file
sed -i 's/foo/bar/g' file
```

## cut

```bash
cut -d: -f1 file
```

## sort

```bash
sort file
sort -n file
sort -r file
```

## uniq

```bash
uniq file
uniq -c file
```

## tr

```bash
tr 'a-z' 'A-Z'
tr -d 'a'
```

## wc

```bash
wc -l file
wc -w file
```

## head / tail

```bash
head -n 5 file
tail -f file
```

---

# Task 6: Useful One-Liners

## Delete old files

```bash
find . -type f -mtime +7 -delete
```

## Count log lines

```bash
wc -l *.log
```

## Replace text

```bash
sed -i 's/old/new/g' *.txt
```

## Check running service

```bash
ps aux | grep nginx
```

## Disk usage alert

```bash
df -h | awk '$5 > 80 {print "High usage:", $0}'
```

## Real-time error monitoring

```bash
tail -f app.log | grep --line-buffered "ERROR"
```

---

# Task 7: Error Handling and Debugging

## Exit Codes

```bash
exit 0
exit 1
echo $?
```

## set -e

```bash
set -e
```

Exit on command failure.

## set -u

```bash
set -u
```

Error on undefined variables.

## set -o pipefail

```bash
set -o pipefail
```

Catch pipeline failures.

## Debug Mode

```bash
set -x
```

## Trap

```bash
trap 'echo "Cleaning up"' EXIT
```

---

# What I Learned

1. Shell scripting basics and automation.
2. Text processing using grep, awk, and sed.
3. Error handling and debugging in Bash.
