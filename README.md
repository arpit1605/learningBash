# Comprehensive Bash Script for Learning Bash Scripting
This README file serves as a practical guide to Bash scripting with diverse examples. Below, I provide a structured overview of the script's contents, categorized by the titles or headings that you've defined with comments in the script.

## Environment Variables
- **Home Variable**: Demonstrates how to use the `$HOME` environment variable to echo the path and list its contents.
- **User and Hostname Variables**: Shows how to handle and display user and system name using `$USER` and `$HOSTNAME`.
- **Avoiding Expansion**: Illustrates using escape characters to prevent variable expansion.

## File and Directory Operations
- **Writing to Files**: Covers creating and writing to files using redirection and the `echo` command.
- **File Touching and Linking**: Demonstrates creating files with `touch` and creating symbolic links with `ln -s`.
- **Changing Permissions and Ownership**: Provides examples on modifying file permissions with `chmod` and changing ownership with `sudo chown`.
- **File Checks**: Includes checking if files exist, their types (like if a file is a symbolic link), and handling file permissions.

## Basic Operations
- **Arithmetic Operations**: Explains basic and advanced arithmetic operations including increments, and operations within brackets.
- **String Operations**: Showcases string concatenation, comparisons, and multi-line strings using HEREDOC.
- **Conditional Statements**: Offers examples of using `if` and `case` statements for numerical and string comparisons.

## Loops and Arrays
- **For Loops**: Various forms of for loops demonstrating list iteration, command output processing, and directory traversal.
- **While and Until Loops**: Usage of while and until loops for condition-based looping and file operations.
- **Array Handling**: Shows both indexed and associative array declaration, manipulation, and access.

## Advanced Scripting
- **Functions**: Definition and usage of functions for performing specific tasks like summing numbers and handling parameters.
- **Terminal Commands**: Use of `tput` for controlling terminal output like setting bold text, and clearing the screen.
- **User Input**: Handling user input with `read` command variations for direct input, arrays, and timed inputs.

## System and Process Handling
- **Executing and Timing Commands**: Examples of executing other scripts, capturing their output, and timing commands.
- **Handling Background Processes**: Demonstrates how to manage background processes using `wait`, `kill`, and checking exit statuses.

## Data Processing
- **Text Processing**: Use of `awk`, `sed`, `grep`, and `cut` for sophisticated text manipulation and data extraction.
- **Sorting and Counting**: Demonstrates sorting files, counting lines, characters, and unique data processing.

## File Compression and Email
- **File Archiving**: Commands for creating tar archives and handling compressed files.
- **Email Handling**: Examples of sending emails from scripts using `ssmtp` and `mutt` with and without attachments.

## Specialized File and System Operations
- **JSON Handling**: Shows how to parse JSON files using `jq` for extracting and printing specific fields.
- **System Information**: Commands to access and display CPU, memory, and network information from system pseudo-files.

## Here is a list of each title in the script and the equivalent Bash commands associated with them:

### Home variable:
```bash
VAR_PATH=$HOME
echo "$VAR_PATH"
ls "$HOME"
```

### USER variable:
```bash
VAR=$USER
echo "$VAR"
```

### HOSTNAME variable:
```bash
VAR=$HOSTNAME
echo "$VAR"
```

### Echo $HOME with Escape to avoid expansion:
```bash
echo "\$HOME"
```

### Write to file in Home directory using $HOME Environment variables:
```bash
cd $HOME
echo "I like Range Rover" > test.txt
cat test.txt
```

### touch command:
```bash
touch filetouch.txt
ls
```

### Create a Symbolic Link to a file, write to the Linked file, Cat Linked file:
```bash
ln -s test.txt link1
ls
echo "I have linked this file and I am writing to this linked file link1" >> link1
cat link1
```

### Give executable file permission to a file:
```bash
chmod +x script.sh
```

### Remove write permission of a file:
```bash
chmod -w filetouch.txt
```

### Change owner of a file:
```bash
sudo chown userid filetouch.txt
```

### Using underscore variable, touch file, use underscore variable to append to it:
```bash
UND_VAR="Hello Audience"
touch new.txt
echo "$UND_VAR" >> new.txt
cat new.txt
```

### Basic Arithmatic operations:
```bash
let num1=3 num2=5 num3=num1+num2
echo "$num1 $num2 $num3"
num1=10
num2=2
expr $num1 + $num2
expr $num1 - $num2
expr $num1 / $num2
expr $num1 \* $num2
expr $num1 % $num2
echo "$(($num1 + $num2))"
echo "$(($num1 - $num2))"
echo "$(($num1 / $num2))"
echo "$(($num1 * $num2))"
echo "$(($num1 % $num2))"
echo "$(($num1 ** $num2))"
```

### Arithmatic operation with Brackets:
```bash
VAR=$((3*(2+1)))
echo $VAR
```

### Increment the VAR by 1:
```bash
VAR=1
VAR=$((VAR+=1))
echo "$VAR"
```

### Concatenate 2 strings:
```bash
VAR1="Hello World!"
VAR2="Let's rule it"
VAR3="${VAR1} ${VAR2}"
echo "${VAR3}"
```

### Concatenate 2 strings using + operator:
```bash
VAR1="Hello World!"
VAR1+="${VAR2}"
echo "${VAR3}"
```

### Create Multi-line string variable using HEREDOC
```bash
VAR1=$(cat<<'END_HEREDOC'
Hi, this is my multi-line string:
My name is TestUser
I am a programmer
END_HEREDOC
)
echo "$VAR1"
```

### Concatenate Multi-line HEREDOC string
```bash
cat<<user-id
The current working directory is: $PWD
You are logged in as: $(whoami)
user-id
```

### IF Conditional Statement with logical AND operator
##### For Textual comparison: (gt, lt, ge, le)
##### For Angular comparison: (<, >, <=, >=, ==)
```bash
MARKS=95
if [[ $MARKS -gt 90 ]] && [[ $MARKS -le 100 ]]
then
	echo "Excellent" 
elif (( $MARKS > 60 )) && (( $MARKS <= 90 ))
then 
	echo "Good"
elif (( $MARKS >= 40 )) && (( $MARKS <= 60 ))
then
	echo "Average"
else 
	echo "Fail"
fi
```

### String comparisions: (==, != and NULL)
```bash
VAR1="Hello"
VAR2="World" 
VAR3="Hello"
VAR4=''
if [ $VAR1 == $VAR3 ]
then 
    echo "Both strings are same"
fi
if [ $VAR1 != $VAR2 ]
then 
    echo "Both strings are not same"    
fi
if [[ $VAR4 = '' ]]
then 
    echo "String is null"
fi
```

### CASE Statement with numeric check:
```bash
VAR=40
case $VAR in 
	10)
		echo "It's 10"
		;;
	20)
		echo "It's 20"
		;;
	30)
		echo "It's 30"
		;;	*)
		echo "Number is not in the list"
		;;
esac
```

### CASE Statement with alphanumeric check:
```bash
VAR="Hyundai"
case $VAR in 
	Hyundai)
		echo "It's Hyundai"
		;;
	MG)
		echo "It's MG"
		;;
	KIA)
		echo "It's KIA"
		;;	*)
		echo "String is not in the list"
		;;
esac
```

### CASE Statement with alphanumeric check:
```bash
case $1 in 
	req*)
		echo "It's request or requirement"
		;;
	meet*)
		echo "It's meeting"
		;;
	*)
    	echo "This is a default statement"
		;;
esac
```

### ******************************* File operations: *******************************
```bash

```

### Check whether file is present or not
```bash
FILE=emptyfile.txt
if [ -f "$FILE" ]
then
	echo "File $FILE exists"
else
	echo "File $FILE doesn't exists"
fi
```

### Check whether file is empty or not
```bash
FILE=new.txt
if [ -s "$FILE" ]
then
	echo "File is not empty"
else
	echo "File is empty"
fi
```

### Check whether input path is a directory or a file:
```bash
PATH=learningBash  # Other inputs are test.txt and dir 
if [[ -d $PATH ]]
then
	echo "$PATH is a directory, not a file"
elif [[ -f $PATH ]]
then
	echo "$PATH is a file, not a directory"
else
	echo "$PATH is not valid"
fi
```

### Check whether input file is a symbolic link or not:
```bash
FILE=link1
if [[ -L "$FILE" ]]
then
	echo "$PATH is a symbolic link"
else
	echo "$PATH is not a symbolic link"
fi
```

### Check for file permissions: (replace -r with -x for execute and with -w for write)
```bash
FILE=new.txt
if [[ -r "$FILE" ]]
then
	echo "$FILE has read permissions"
else
	echo "$FILE doesn't have read permissions"
fi
```

### Execute a script and capture STDOUT, STDERR and Return code:
```bash
./script.sh
if [ $? -eq 0 ]
then 
    echo "Script executed successfullly" > output.txt
else 
    echo "$?" > error.txt
fi
```

### Write the output of the script in a temp file using exec command:
```bash
exec > tmp
echo "Hello World"
ls
```

### EVAL command:
```bash
eval echo "Hello World"
```

### For Loop List of Values:
```bash
for i in 1 2 3 4 5; 
do
    echo "The value is: $i"
done
```

### For Loop with Conditional Break and Continue:
```bash
for i in {1..10}; do
  if (( $i <= 4 )); then
     echo "$i"
  elif (( $i ==  5 )); then
     continue
  else
    break;
  fi
done
```

### For Loop Output of Command:
```bash
for i in $(cat test.txt); do
    echo "$i"
done
```

### For Loop Files in Directory:
```bash
for i in ./*.txt; do
    echo "$i"
done
```

### While Loop With Integer Counter:
```bash
i=0
while (( ++i <= 5)); do
  echo "Counter is at: $i"
done
```

### Until Loop Based on File Size:
```bash
Can you explain the below bash script in detail:
FILENAME=`basename "$0"`
echo $FILENAME
TMP_FILE="./tmp1"
TARGET_FILE="./target"
cat $FILENAME > $TARGET_FILE
FILESIZE=0

until [ $FILESIZE -gt 20 ]; do
  cp $TARGET_FILE $TMP_FILE
  cat $TMP_FILE >> $TARGET_FILE
  FILESIZE=`du $TARGET_FILE | awk '{print $1}'`
  echo "size of file: $FILESIZE Bytes"
  sleep 1
done

echo "New size of file exceeded target of 20B+"
```

### Create an Array Variable and access each element by Index using for loop:
```bash
car=('BMW' 'Mercedes' 'Tesla' 'Audi' 'Ferrari')
for i in "${car[@]}"; do
  echo "$i"
done
```

### Create an Associative Array Variable Access by Index:
```bash
declare -A car
car[BMW]=i8
car[Toyota]=Corrola
car[Honda]=Civic
car[Mercedes]=Benz
echo "${car[Honda]}"
```

### Time a Command
```bash
time ./mybashfile.sh
```

### Print Date
```bash
VAR=$(date)
echo "$VAR"
```

### Print Date With Format
```bash
VAR=$(date +%F)
echo "$VAR"
VAR=$(date +%D)
echo "$VAR"
VAR=$(date +%Y)
echo "$VAR"
```

### Print Seconds Elapsed for Block of Code:
```bash
TIMEFORMAT="It takes %R seconds to complete this task..."
time {
  for i in {1..20}; do
      echo "writing code in curly braces to calculate time"
  done
}
```

### Read Text From File, Print only the first 2 lines using If Condition:
```bash
FILE='file.txt'
n=1
while read line; do
  echo "Line-$n : $line"
  n=$((n+1))
  if ((n>2)); then
     break;
  fi
done < $FILE
```

### Basic Read Command:
```bash
echo "Please enter 3 words that describes you followed by ENTER:"
read first second third
echo "Hello! you are $first, $second, and $third"
```

### Read Command Into Array:
```bash
echo "Give input you want to store into an array"
read -a arrayVar
echo "The input array members are as follows:"
for i in ${arrayVar[@]}; do
  echo "$i"
done
```

### Read Command with Delimiter
```bash
echo "Enter the car and it's model:"
IFS='|' read car model <<< 'BMW|i8'
echo "Hello, car is $car and model is $model"
```

### Read Command with Timeout:
```bash
date 
read -t 14 -p "Please enter key or wait for 14 seconds:"
```

### Menu Option with Select Command:
```bash
PS3="Please choose a car manufacturing company:"
cars=("BMW" "Toyota" "Honda" "Quit")
select car in "${cars[@]}"
do
  case $car in
     "BMW")
       echo "You choose BMW"
       ;;
     "Toyota")
       echo "You choose Toyota"
       ;;
     "Honda")
       echo "You choose Honda"
       ;;
     "Quit")
       break
       ;;
  *) echo "Invalid Option $REPLY";;
  esac
done
```

### Menu Option With Select Command From Array Variable:
```bash
PS3="Please choose a car manufacturing company:"
menu_from_array()
{
    select item; do
        if [ 1 -le "$REPLY" ] && [ "$REPLY" -le $# ]; then
            echo "The selected car company is $item"
            break;
        else
            echo "Wrong selection! Select any number from 1-$#"
        fi
    done
}
cars=("BMW" "Toyota" "Honda")
menu_from_array "${cars[@]}"
```

### Split String By Space:
```bash
line="This is a line which has spaces in between"
for word in $line; do
    echo "$word"
done
```

### Split String By Custom Delimiter:
```bash
line="This!is!a line!which has!spaces in!between"
#echo "$line" | sed 's/[! ]/\n/g'
#echo "$line" | tr '! ' '\n'
delimiter='!'
IFS="$delimiter" read -r -a array <<< "$line"

for element in "${array[@]}"; do
    echo "$element"
done
```

### Split String by Multi-Byte Delimiter:
```bash
line="WeXYZareXYZhereXYZtoXYZsplitXYZtheXYZstring"
delimiter="XYZ"
mArr=()
while [[ $line ]]; do
    # Find the position of the delimiter
    pos=$(expr index "$line" "$delimiter")
    if [[ $pos -gt 0 ]]; then
        # Extract the substring before the delimiter
        mArr+=("${line:0:pos-1}")
        # Remove the processed part from the line
        line=${line:pos+${#delimiter}-1}
    else
        # Add the remaining part of the line
        mArr+=("$line")
        break
    fi
done
declare -p mArr
```

### Parse Command Line Options With Shift Command:
```bash
shift 1      # Shifts the number of input
echo 0=$0    # Prints the Bash script file name
echo 1=$1
echo 2=$2
echo 3=$3
```

### Parse Command Line Using GetOpt:
```bash
while getopts 'xyz:' OPTION; do
    case "$OPTION" in
        x) echo "this is x" ;;
        y) echo "this is y" ;;
        z) echo "The value provided is $OPTARG" ;;
        ?) echo "script usage: $(basename $0) [-x] [-y] [-z]" >&2 ;;
    esac
done
shift "$((OPTIND - 1))"
```

### Read Password from Stdin, Without Printing it:
```bash
echo -n "Enter a password:"
read -s password
echo " "
echo "The password you have entered is: $password"
```

### Pipe Command Sort Example:
```bash
cat car.txt | sort
```

### Cat Pipe Word Count Example:
```bash
cat car.txt | wc -w
```

### read from STDIN, send data with Pipe:
```bash
cat car.txt | while read line ; do
echo $line ; done | cat > new.txt
```

### Echo to BC Command for Math Expression Simple:
```bash
num1=10
num2=20
echo $num1 + $num2 |bc
```

### Function Prints Common Text, Call Multiple Times:
```bash
function func()
{
    name="Fname1 Lname1"
}
name="Fname2 Lname2"
echo $name
func
echo $name
```

### Function Takes Params, Returns Sum:
```bash
function sum()
{
    sum=$(($1 + $2))
    echo "Sum is: $sum"
}
sum 3 4
```

### Tput Command to Print String:
```bash
tput bold
echo "This is tput command to print the string in bold"
```

### Tput Command:
```bash
tput -V # Print Attributes of Terminal Simple:
tput lines # Get the number of lines (height) of the terminal
tput cols # Get the number of columns (width) of the terminal
tput colors # Get the number of colors
tput longname # Get the long name of the terminal type
tput clear  # Clear the screen
tput bold  # Set text to bold
tput dim # Enable dim text
tput cup 10 20  # Move the cursor to row 10, column 20
tput setaf 1 # Set the color of text to red
tput sgr0 # Reset text attributes
tput cud1 # Move the cursor to the next line
```

### Assign String Variable with Declare:
```bash
declare var="string variable with declare"
```

### Check If Variable Created with Declare:
```bash
declare var="string variable with declare"
echo $var
if [ -z ${var+a} ]; then
    echo "variable is not declared"
else    
    echo "variable is declared and set to '$var'"
fi
```

### n Option for Declare to Nameref Alias:
```bash
bar=a
declare -n foo=bar
echo ${foo} ${bar}
foo=b
echo ${foo} ${bar}
true
```

### Forcing Variable to Integer with Declare:
```bash
str=2
declare -i str=$((${str#0}+1))
echo $str
```

### Forcing Case with Declare:
```bash
number=array
case $number in 
    array)
        declare -i n[0]=4
        declare -i n[1]=6
esac
echo ${n[0]}
```

### Readonly Variables with Declare:
```bash
declare -r author='testuser'
author="someone"
echo $author
```

### Indexed Arrays with Declare:
```bash
declare -a array
array=(linux windows mac)
echo ${array[0]}
echo ${array[@]}
```

### Associative Arrays with Declare:
```bash
declare -A array
array=([website]=Youtube [channel]=LinuxHunt)
echo ${array[website]}
echo ${array[channel]}
echo ${array[@]}
```

### Automatically Answer Question with yes Command:
```bash
yes | cp -i file.txt new.txt
```

### Use And Operator to Run Second Command Only if First Succeeds:
```bash
s1=4
s2=8
if [[ ($s1 -gt $s2) && ($S1 -eq 4)]]; then
    echo "condition passed"
else
    echo "condition failed"
fi
```

### Use Or Operator to Run Second Command Only if First Fails:
```bash
s1=12
s2=8
if [[ ($s1 -gt $s2) || ($S1 -eq 4)]]; then
    echo "condition passed"
else
    echo "condition failed"
fi
```

### xargs to operate on all files in directory:
```bash
ls *.txt* | xargs wc
```

### Wait For Another Command to Complete:
```bash
echo "testing wait command 1" &
process_id=$!
echo "testing wait command 2" &
wait $process_id   # When this line is commented out, the sequence of echo commands executed is different
echo "command 1 completed"
echo "command 2 completed"
```

### Combine Kill and Wait Commands:
```bash
echo "testing wait command"
sleep 30 & 
pid=$!
kill $pid
wait $pid
echo "$pid was terminated"
```

### Star Wildcard on File Selection:
```bash
ls -l file*
```

### Question Mark Wildcard on File Selection:
```bash
ls -l fi?e.txt
```

### Square Bracket on File Selection:
```bash
ls -l file[12].txt
```

### Parenthesis and Pipe for File Selection Options:
```bash
ls -l [f-z]* | wc -l
```

### Brace Expansion Comma Seperated List:
```bash
echo Linux{1,2,3} | tr ' ' ,   # Translate Space with a Comma
echo Linux{A,B,C} | tr ' ' ,
```

### Brace Expansion Range:
```bash
echo {M..Z}
echo {A..E}{1..5}
```

### Operating on List of Files with Brace Expansion:
```bash
mkdir "dir"{4,5,6}   # creates directories with names dir4, dir5 and dir6
ls
```

### Reference Home Directory with Tilde:
```bash
echo ~   # echo the home directory
```

### Substring Expansion for Printing Part of String:
```bash
string="United States of America"
echo $string
echo "${string:0:6}"
```

### Parameter Expansion for Assigning Constant to Variable if Unset:
```bash
echo "${checkVar:-unset}"
echo "lets assign it a value"
echo "${checkVar:=bash}"
```

### Check If File Executable, Set If Not:
```bash
file="new.txt"
if [[ -x "$file" ]]; then
    echo "File is executable"
else
    echo "File is not executable"
    chmod +x $file
    echo "File is executable now"
fi
```

### Check If File Is Owned By User, Set If Not:
```bash
file="new.txt"
if [[ -O "$file" ]]; then
    echo "File is owned by the currently logged in user"
else
    echo "File is not owned by the currently logged in user"
    sudo chown testuser $file
    echo "File is owned by the currently logged in user now"
fi
```

### wc To Count Lines and Characters In A File:
```bash
echo "The number of lines and character in a file are:"
wc -l -c file.txt
```

### ls pipe and wc to count files in a directory:
```bash
ls | wc -l
```

### ls pipe and wc to count number of lines and characters in all files present in a directory:
```bash
ls | wc -l -c *
```

### Head Command With Default Args:
```bash
file="new.txt"
sudo head $file
```

### Head Command to Print First 3 Lines:
```bash
file="new.txt"
sudo head -n 3 $file
```

### Tail Command With Default Args:
```bash
file="new.txt"
sudo tail $file
```

### Tail Command to Print Last 100 Lines:
```bash
file="new.txt"
sudo tail -n 2 $file
```

### Find Command to Locate Matching Pattern Files:
```bash
find . -name *e*.txt -print
```

### Find Command to Locate Files Based on Date:
```bash
find . -name new.txt -type f -ls | grep 'Aug 25'
```

### cut Command to Parse Delimited Columns of Data:
```bash
cut -f 2-3 new.txt
```

### grep Command to Search for Pattern
```bash
grep HONDA new.txt
```

### grep Command to Search for Case Insensitve Pattern
```bash
grep -i honda new.txt
```

### grep Command to Search for Lack of Pattern
```bash
grep -v HONDA new.txt
```

### grep Command with Wild Cards
```bash
grep -i hon* new.txt
```

### grep Command to Search All Files in Directory Recursive:
```bash
grep -r HON*
```

### grep Command to Search for File in a Directory Recursively:
```bash
grep -rl HON*
```

### awk with Variable:
```bash
awk 'BEGIN{ site="testuser"; print site}'
```

### awk Split On Whitespace:
```bash
awk '{ print $2 " " $3 }' new.txt
```

### awk Print Last Field in Each Line:
```bash
awk '{ print $NF }' new.txt
```

### awk with custom delimiter:
```bash
awk '$1=$1' FS=" " OFS="-" new.txt
```

### awk Print Only Match of Regex:
```bash
awk '/HO/' new.txt
```

### awk With If Else Condition:
```bash
awk '{
    if($1=="MG")
    {
        print "Yes, it is.", "\n"
    }
    else
    {
        print "No, it is not.", "\n"
    }
}' new.txt
```

### awk With Ternary Operator:
```bash
awk '{
    print ($1=="MG") ? "Yes, it is." : "No, it is not."
}' new.txt
```

### sed To Replace Matching Text:
```bash
sed 's/HONDA/CORROLA/' new.txt
```

### sed To Replace Second Instance of Matching Text on Line:
```bash
sed 's/HONDA/CORROLA/2' new.txt
```

### sed to Delete Specific Lines:
```bash
sed '2d;3d' new.txt
```

### sed to Permanently delete Specific Lines:
```bash
sed -i '2d;3d' new.txt
```

### sed to Add a Line Before Matched Line:
```bash
sed '/^MG*./i Before' new.txt
```

### sed to Add a Line After Matched Line:
```bash
sed '/^MG*./a After' new.txt
```

### Sort Data in File with sort Command:
```bash
sort new.txt
```

### Sort Data Ignore Case:
```bash
sort -f new.txt
```

### Sort Data numerically:
```bash
sort -n numbers.txt
```

### Print Unique Data with uniq Command:
```bash
uniq new.txt        # Print unique lines
uniq -c new.txt     # Print unique lines with count 
uniq -cd file.txt   # Print duplicate lines with count
```

### Count Unique Lines in File with Sort, Uniq, and wc:
```bash
echo "Enter the filename"
read fileName
if [[ -f "$fileName" ]]; then
    sort $fileName | uniq -c | sort -bgr
else
    echo "$fileName doesn't exists"
fi
```

### Convert Data to Uppercase with tr:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    tr '[a-z]' '[A-Z]' < $fileName
else
    echo "$fileName doesn't exists"
fi
```

### Convert Data to Lowercase with tr:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    tr '[A-Z]' '[a-z]' < $fileName
else
    echo "$fileName doesn't exists"
fi
```

### Create a tar File:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    tar -cvzf $fileName.tar $fileName --remove-files
    #tar -cvzf $fileName.tar $fileName     ## If you would like to retain the original file as well
else
    echo "$fileName doesn't exists"
fi
```

### Create a Zipped Tar File with 'gz' extension:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    tar -cvzf $fileName.tar.gz $fileName --remove-files   
else
    echo "$fileName doesn't exists"
fi
```

### Unzip a Compressed Tar File:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    tar -xzf $fileName
else
    echo "$fileName doesn't exists"
fi
```

### Parse JSON File with jq:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    cat $fileName | jq '.'
else
    echo "$fileName doesn't exists"
fi
```

### Print Specific Field in JSON with jq:
```bash
echo "Enter filename"
read fileName
if [[ -f "$fileName" ]]; then
    jq '.glossary.title' $fileName
else
    echo "$fileName doesn't exists"
fi
```

### Print Cpu Info With Pseudo Filesystem:
```bash
cat /proc/cpuinfo
```

### Print Mem Info With Psuedo Filesystem:
```bash
cat /proc/meminfo
```

### Print Mounts With Psuedo Filesystem:
```bash
cat /proc/mounts
```

### Print Network Stats With Psuedo Filesystem:
```bash
cat /proc/net/netstat
```

### Print Disk Usage with du:
```bash
du /home/xyx/learningBash
```

### Print Disk Usage summary with du:
```bash
du -s /home/testuser/learningBash
```

### Print Disk Usage Human Readable with du:
```bash
du -h /home/testuser/learningBash
```

### Create File of Specified Size with dd:
```bash
dd if=/dev/zero of=myfile.txt count=1 bs=1024
```

### Time Disk Writing with dd and time:
```bash
dd if=/dev/zero of=myfile.txt count=1 bs=1024 oflag=dsync
```

### Send a Mail with mail Program:
```bash
sudo apt-get update
sudo apt-get install ssmtp -y
sudo apt-get install gedit -y 
    # Script to send an email using ssmtp
TO="example1@gmail.com" "exanple2@gmail.com"
FROM="test@gmail.com"
CC="example@gmail.com"
BCC="example3@gmail.com"
SUBJECT="Test Email"
BODY="This is a test email sent from a bash script using ssmtp."
echo -e "To: $TO\nSubject: $SUBJECT\n\n$BODY" | ssmtp $TO

    # Execute the command sudo nano /etc/ssmtp/ssmtp.conf and perform the configuration as below:
root=postmaster
mailhub=smtp.mail.yahoo.com:587
hostname=name-of-host.
AuthUser=example@yahoo.com
AuthPass=email-password
UseSTARTTLS=yes
```

### Send a Mail with mail Program with Encoded Attachment:
```bash
sudo apt-get update
sudo apt-get install mutt -y
echo "This is a test email. \nI have attached a list of Car manufacturing companies." | mutt -a "new.txt" -s "File Attachment" -- example@gmail.com
echo "Email sent successfully"
```

### Print Mounts Usage with df:
```bash
df -a
```

### Download Webpage with Curl:
```bash
curl https://www.google.com --output googlePage.txt
```

### Post to HTTP with Curl:
```bash
curl -X POST -d @googlePage.txt http://www.google.com
```

### Put Command in Background:
```bash
sudo apt update &
```

### Resume Command From Background:
```bash
fg
```

### Execute Last Command Again with Bang Bang:
```bash
!!
```

### tee Command to Print to File and Screen:
```bash
tee -a new.txt
```
