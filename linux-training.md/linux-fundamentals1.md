# Linux Basics – Quick Notes

## Navigation
pwd shows the current directory (example: /home/tryhackme/folder4)
cd and ls are used to move between directories and list files

## Finding Files
find -name password.txt
find -name "*.txt"
find -name "password*"

## Searching Content (grep)
grep "something" filename.txt
grep -R "something" /etc/

-R means recursive (searches inside all subdirectories)

## Operators
& runs a command in the background
&& runs the second command only if the first one succeeds

Example:
command1 && command2

## Output Redirection
echo "hello am walid heree" > intro

> creates or overwrites a file
>> appends to a file without deleting existing content
