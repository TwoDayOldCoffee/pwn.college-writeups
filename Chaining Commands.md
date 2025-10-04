### Chaining with Semicolons
```pwn.college{0mKaOwSxnLwqYyI6-sYtp1f_pQ-.dVTN4QDL1gTN0czW}```

; is used to denote the end of a command (similar to how its used in java or C)  
```~$ /challenge/pwn; /challenge/college```

### Building on Success
```pwn.college{823ZC3WD3MxJ9CiYtfFAOMx7okk.QXyQzM4EDL1gTN0czW}```

We can use the ```&&``` operator to chain together 2 commands. The operator will run the second command only if the first command succeeds.  
For this challenge- ```~$ /challenge/first-success && /challenge/second``` will give us the flag.  

### Handling Failure
```pwn.college{w2S-1lq2S1tk4xDpVhoXOMnfzsG.QXzQzM4EDL1gTN0czW}```  

The ```||``` operator will run the second command only if the forts command is a failure.  
For this challenge- ```~$ /challenge/first-failure || /challen``` will give us the flag.  

### Your First Shell Script
```pwn.college{8SP8fqKoCWSMv8BBNrjQMC86F1A.dFzN4QDL1gTN0czW}```

To know about how to make a shell script- https://www.geeksforgeeks.org/how-to-create-a-shell-script-in-linux/  
```~$ touch x.sh``` This command will make a shell script  
```~$ chmod +x x.sh``` This command makes the shell script executable.  
```~$ nano x.sh``` This command opens up the shell editor.  
In the shell editor we add the two commands that need to be run and exit it.  
```~$ bash x.sh``` will now give us the flag

### Redirecting Script Output
```pwn.college{QlWDucPhLOYd5w52OTaMXEzbeQL.dhTM5QDL1gTN0czW}```

Similar to the previous challenge but we need to pipe to output to a command.  
```
~$ touch x.sh  
```~$ chmod +x x.sh  
```~$ nano x.sh
~$ bash x.sh | /challenge/solve
```  
Will now give us the flag

### Executable Shell Scripts
```pwn.college{Q4rPfyoJQ8fvz1i7CQoQD6Xs5K7.dRzNyUDL1gTN0czW}```

If can make the shell executable, then we wont have to use to bash to command to run it. A shell can be made executable using ```~$ chmod +x script.sh```  
```
~$ touch script.sh  
```~$ chmod +x script.sh  
```~$ nano script.sh
~$ script.sh
```

### Understanding Shebangs
```pwn.college{QawKOicP9NMzQIqwxGo03I1ZLs4.QX5MzM4EDL1gTN0czW}```

```
~$ cd /home/hacker
~$ touch solve.sh
~$ printf '%s\n' '#!/bin/bash' "printf 'hack the planet\n'" > solve.sh
~$ chmod a+x solve.sh
~$ /challenge/run
```  
Will give us the answer.  
```~$ printf '%s\n' '#!/bin/bash' "printf 'hack the planet\n'" > solve.sh``` adds the shebang and print statement needed into the file.  
We then make the file executable by all and that gives us the answer.  

### Scripting with Arguments
```pwn.college{YjXa2fQ3kSOCGwiBDSXqFaWrSvO.QX1MzM4EDL1gTN0czW}```  

```
~$ printf '%s\n' '#!/bin/bash' 'echo "$2 $1"' > /home/hacker/solve.sh
~$ /challenge/run
```
Will give us the answer. $ is used to refer to the arguments passed to a script.  

### Scripting with Conditionals
```pwn.college{kpr49lBhXjhzykn414e0Hc0Hf1_.QX2MzM4EDL1gTN0czW}``` 

```
~$ printf '%s\n' '#!/bin/bash' 'if [ "$1" == "pwn" ]' 'then' 'echo "college"' 'fi' > /home/hacker/solve.sh
~$ /challenge/run
```
The above code implements the conditional statement required in this problem.  

### Scripting with Default Cases
```pwn.college{8ol0OcQ-X6WCvLwsydw-Se-M67c.QX3MzM4EDL1gTN0czW}```

```
~$ printf '%s\n' '#!/bin/bash' 'if [ "$1" == "pwn" ]' 'then' 'echo "college"' 'else' 'echo "nope"' 'fi' > /home/hacker/solve.sh
~$ /challenge/run
```
This implements an if-else code in a bash script for this problem.  

### Scripting with Multiple Conditions
```pwn.college{o93ipAsOCY4RVcKGf8Dhp1BCiuo.QX4MzM4EDL1gTN0czW}```

```
~$ printf '%s\n' '#!/bin/bash' 'if [ "$1" == "hack" ]' 'then' 'echo "the planet"' 'elif [ "$1" == "pwn" ]' 'then' 'echo "college"' 'elif [ "$1" == "learn" ]' 'then' 'echo "linux"' 'else' 'echo "unknown"' 'fi' > /home/hacker/solve.sh
~$ /challenge/run
```
This implements the if-elif-else code necessary to finish this problem. 

### Reading Shell Scripts
```pwn.college{0FkrBaigHVwcOrCTeKpu3lX-Qon.QXyADO4EDL1gTN0czW}```
```~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
```
Catting the contents of the file tells us the password needed. 
```
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
```
Will give us the flag.  

