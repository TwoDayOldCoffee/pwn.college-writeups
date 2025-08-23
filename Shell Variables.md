### Printing Variables
```pwn.college{QiyJ9-d0xyTAY-mP_bqlHDUD06N.ddTN1QDL1gTN0czW}```  

the echo command will print the variable we want if we prepend the variable name with '$'  
```~$ echo $FLAG```

### Setting Variables
```pwn.college{IGDJ03KBeOxrbNbXgyBqg4fDvtN.dlTN1QDL1gTN0czW}```  

we can assign values to a variable  
```PWN=COLLEGE```

### Multi-Word Variables
```pwn.college{sYwTdQkDpP93ue2PjpJttJGbgOk.dBjN1QDL1gTN0czW}```  

We can have empty spaces while initialising a variable bcuz the shell will take the second word to be a command. Hence we need to use double quotes similar to using a string.  
```pwn.college{sYwTdQkDpP93ue2PjpJttJGbgOk.dBjN1QDL1gTN0czW}```

### Exporting Variables
```pwn.college{Ig3ldrgTlvqynO_QED_jB1PQuzj.dJjN1QDL1gTN0czW}```

In this challenge we need to invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported.  
The export command is used for security reasons.  
```  
~$ export PWN
~$ PWN=COLLEGE
~$ COLLEGE=PWN
~$ /challenge/run
```
gives us the flag

### Printing exported variables
```pwn.college{gEdNveeW9RIufExsbeLi7vu_1Ax.dhTN1QDL1gTN0czW}```  

The 'env' variable is used to print all the exported variables  
```~$ env``` 

### Storing Command Output
```pwn.college{E6c6tMQYyCWvyKzDAaQ6ROCCCBw.dVzN0UDL1gTN0czW}```

We can assign the output of a command to a variable using $().  
```
~$ PWN=$(/challenge/run)
~$ cat $PWN
```

### Reading Input
```pwn.college{45QwjFP2j-xsCXkKxvOt8apd53M.dhzN1QDL1gTN0czW}```

The 'read' command lets us input a value using stdin. The '-p' argument is used to give a prompt.  
```
~$ read -p "INPUT: " PWN
INPUT: COLLEGE
```  

### Reading Files
```pwn.college{cGlsfff4nuS04wfBRRFA6KSrLLN.dBjM4QDL1gTN0czW}```

We can input file contents into a variable using '<'  
```~$ read PWN < /challenge/read_me```  




