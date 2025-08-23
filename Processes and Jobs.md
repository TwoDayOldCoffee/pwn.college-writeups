### Listing Processes
```pwn.college{AdlR-bJ9lwViivsPoPei_8jLYWg.dhzM4QDL1gTN0czW}```

We can use the ps -ef command to see all the running processes to find the program in /challenge which is running and will give us the flag.  
running ```~$ ps -ef``` shows us the list of processes one of which is ```/challenge/25442-run-19496``` and is the programm we are looking for  '
```~$ /challenge/25442-run-19496```  
Will give us the flag  

### Killing Processes\
```pwn.college{ECfJ2XFNAq2N3RLPDI4yCtvtas0.dJDN4QDL1gTN0czW}```  

We can kill a process using its PID and the 'kill' command.  
To solve this challenge we need to find the PID of '/challenge/dont-run' by using 'ps -ef' and then killing it before using 'challenge/run' to find the flag  
```
~$ ps -ef
~$ kill 73
~$ /challenge/run
```  
will give us  the flag

### Interrupting Processes
```pwn.college{cbMw69lZS4wKBO-En14o1Tuk0fD.dNDN4QDL1gTN0czW}```

We use Ctrl-C to interrupt a process  
```
~$ /challenge/run
^C
```  
Will give us the flag

### Suspending Processes
```pwn.college{QTuiBLvFlqMeFI9Mpl1hyF7Vb2a.dVDN4QDL1gTN0czW}```

We can use Ctrl-Z to suspend a process in the background. This allows us to run the same process multiple times at the same time.  
This is exactly what we need to do for this challenge.  
```
~$ /challenge/run
^Z
~$ /challenge/run
```  
Will give us the flag

### Resuming Processes
```pwn.college{s7lT3RJM3sW_jogjpWPWxRz8yOj.dZDN4QDL1gTN0czW}```

We can use the 'fg' command to resume a suspended process (and run the program in the foreground).  
```
~$ /challenge/run
^Z
~$ fg /challenge/run
```  
Should give us the flag

### Backgroundign Processes
```pwn.college{cyrCfY4sGOb38BXAm7CaBkzJN9h.ddDN4QDL1gTN0czW}```

We can use the 'bg' command to resume a suspended process (and run the program in the background).  
In this challenge we will get the flag if we run the program with the program also being run in the background.  
```
~$ /challenge/run
^Z
~$ bg /challenge/run
~$ /challenge/run
```
Will give us the flag.

### Foregrounding Processes
```pwn.college{M3VJWYn9laXumPUqRAt0Yl0S-0e.dhDN4QDL1gTN0czW}```

In this challenge we need to use 'fg' to foreground a process which is already running in the background.  
```
~$ /challenge/run
^Z
~$ bg /challenge/run
~$ fg /challenge/run
```
Will give us the flag

### Starting Backgrounded Processes
```pwn.college{klljVJLXsUUGSDrHH34W-og87-Q.dlDN4QDL1gTN0czW}```

We can append '&' to the program to to background a process without having to suspend it first.  
```~$ /challenge/run &``` will give us the flag

### Process Exit Code
```pwn.college{gZV5uCuB_QaKlZrogOQkkDIaSK-.dljN4UDL1gTN0czW}```

In this challenge we need to find the exit code for '/challenge/get-code' and then run '/challenge/submit-code' with that error code as an argument.  
The exit code is stored in '?'  
```
~$ /challenge/get-code
~$ /challenge/submit-code 28
```
Will give us the flag  


