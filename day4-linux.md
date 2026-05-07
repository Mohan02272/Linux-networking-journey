## Linux Scripting & Automation


# Bash Scripting Basics

Bash scripting is writing a set of Linux commands in a file so they can be executed automatically.

#!/bin/bash
echo "Hello World"

#!/bin/bash → tells system to use Bash interpreter
echo → prints output


chmod +x script.sh
./script.sh
chmod +x → gives execute permission
./script.sh → runs script

Variables
name="Mohan"
echo $name

Key Rules:
No space around =
Use $ to access variable

read name
echo "Hello $name"
read → takes input from user

Conditional Statements
if [ $num -gt 10 ]
then
  echo "Greater"
else
  echo "Smaller or equal"
fi

#Operators:

Meaning	Operator
Equal	-eq
Not equal	-ne
Greater	-gt
Less	-lt


Loops
For Loop
for i in 1 2 3
do
  echo $i
done
While Loop
count=1
while [ $count -le 5 ]
do
  echo $count
  ((count++))
done


Functions
myfunc() {
  echo "Function running"
}

myfunc

Practical Example (Backup Script)
#!/bin/bash
src="/home/mohan"
tar -czf backup.tar.gz $src
echo "Backup completed"


#  Scheduling Jobs (Cron)


Cron is a scheduler used to run scripts automatically at specific times.

Open Cron Editor: crontab -e
2.3 Cron Format
* * * * * command
| | | | |
| | | | └── Day of week (0–7)
| | | └──── Month (1–12)
| | └────── Day of month (1–31)
| └──────── Hour (0–23)
└────────── Minute (0–59)

Common Examples
Run every minute: * * * * * /home/mohan/script.sh
Run daily at 2 AM: 0 2 * * * /home/mohan/backup.sh
Run every Sunday: 0 0 * * 0 /home/mohan/cleanup.sh



To view jobs : crontab -l 
To rmeove jobs: crontab -r   



#  Environment Variables

An environment variable is a key-value pair used by the system to store configuration values.

Viewing Variables : printenv
echo $HOME
echo $PATH


Common Variables
Variable	Meaning
HOME	User home directory
USER	Current username
PATH	Command search paths
 

Creating Variables
name="Mohan"
echo $name

 Exporting Variables
export name="Mohan"



