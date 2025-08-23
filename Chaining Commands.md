### Chaining with Semicolons
```pwn.college{0mKaOwSxnLwqYyI6-sYtp1f_pQ-.dVTN4QDL1gTN0czW}```

; is used to denote the end of a command (similar to how its used in java or C)  
```~$ /challenge/pwn; /challenge/college```

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



