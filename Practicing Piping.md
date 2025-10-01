### Redirecting Output
```pwn.college{4yn6UHL82mj7Kx_RKRLfBWELyeX.dRjN1QDL1gTN0czW}```  

the '>' character redirects the output of any command to any file we want.  
```~$ echo PWN > COLLEGE```  
Here we're redirecting the output of 'echo' which is "PWN" to the file 'COLLEGE'. If the file COLLEGE didnt already exist then '>' will create the file  
This command will give us the flag  

### Redirecting more Output
```pwn.college{40ZesCV50pbqGxPUNHG0iEdsqlr.dVjN1QDL1gTN0czW}```

Since we '>' character will redirect the output of any command to any file we can use it to redirect the flag value to a file and then read it from there  
```~$ /challenge/run > myflag```  
This gives an error saying we need to redirect it to the file- '/home/hacker/myflag'
```
~$ /challenge/run > ~/myflag
~$ cat ~/myflag
```
This will give us the output  

### Appending Output
```pwn.college{8ARLEzeMgXwid75RyXZfhRgV3Th.ddDM5QDL1gTN0czW}```

the '>>' character works the same way as the '>' character but it appends the data instead of creating a new output file  
In this challenge the flag has been split into 2 parts and must be added to the 'the-flag' file  
in order to get both the parts without losing the first one, we need to use '>' first followed by '>>'  
```
~$ /challenge/run > ~/the-flag
~$ /challenge/run >> ~/the-flag
```
This gives us the entire flag  

### Redirecting Errors
```pwn.college{gZREdiLPYeRoiqOOKY2i4XicAct.ddjN1QDL1gTN0czW}```

FD describes the communication channel-  
0=stdin   1=stdout   2=stderr  
we can use multiple in the same command  
we need to redirect the output to 'myflag' and rhe errors to 'instructions'  
this will put the flag value in 'myflag' which can then be accessed  
```
~$ /challenge/run >myflag 2>instructions
~$ cat myflag
```  
Will give us the flag  

### Redirecting Input
```pwn.college{Ap16LbNd-QNFKTroFTrg0lafCWa.dBzN1QDL1gTN0czW}```

We need to redirect the PWN file to '/challenge/run' and PWN must contain the value 'COLLEGE'  
first we need to change the value in PWN to COLLEGE and then redirect it into the program  
```
~$ echo COLLEGE > PWN
~$ /challenge/run < PWN
```
This will give us the flag 

### Grepping Stored Results
```pwn.college{4DUIcgVJg_gljT-2O-RGO_oJmKx.dhTM4QDL1gTN0czW}```

In this challenge we need to redirect the output of /challenge/run to /tmp/data.txt and then use 'grep' to find the flag in it  
-grep is a command used for searching and matching text patterns in files contained in the regular expressions, To know more- https://www.geeksforgeeks.org/grep-command-in-unixlinux/  
```
~$ /challenge/run > /tmp/data.txt
~$ grep -i "pwn.college" /tmp/data.txt
```
this grep command searches for the string "pwn.college" in the file and will output the line it is in.  
the '-i' argument enables to search for a string case insensitively in the given file.  
The above commands will give us the flag as the output.

### Grepping Live Output
```pwn.college{wrUTgs9i0xyBcUPFJjL3fIHPq8I.dlTM4QDL1gTN0czW}```

the | operator connects the stout of the command on the left to the stdin of the command on the right.  
We need to run '/challenge/run' and grep its output real time to give us the flag  
```~$ /challenge/run | grep -i "pwn.college"```  
This command gives us the flag directly  

### Grepping errors
```pwn.college{YREwVjrgf0Zz5X7JcbIZD2U-hj3.dVDM5QDL1gTN0czW}```  

Since the | operator only redirects the stdout and not the stderr, we need to use the  >& operator, which redirects a file descriptor to another file descriptor.  
Hence,  we can have a two-step process to grep through errors.  
First we redirect standard error to standard output and then pipe it to grep too search for the flag  
```~$ /challenge/run 2>&1 | grep -i "pwn.college"```  
This gives us the flag directly as the output.  

### Filtering with grep -v  
```pwn.college{01QZkyD5oCpHa3OC5MigtciezBZ.QX4ETM3EDL1gTN0czW}```  

The ```-v``` option inverts the functionality of the grep command.  
In this problem we can use ```~$ /challenge/run | grep -v DECOY``` to filter out the decoy flags and get the right one.  

### Duplicating piped data with tee  
```pwn.college{wbQzaoW6sUCfS1Xx87IqC1NM0NB.dFjM5QDL1gTN0czW}```

In this challenge we need to use tee to intercept the data and find out how to run the command to get the flag.  
To do this we will use tee to store the error given by the command into a file and then hopefully the error stored will give us a clue.  
```~$ /challenge/pwn | tee pwn_output | /challenge/college```  
This gives us the output-  
```
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "wbQzaoW6"
```
The error now tells us what we need to do to get the flag, hence-  
```~$ /challenge/pwn --secret wbQzaoW6 | /challenge/college```  
Will give us the flag.  


### Process Substitution for Input
```pwn.college{ErWTySELtcVH0mgHJUN1tdigFdp.QX2AzM4EDL1gTN0czW}```  

Since linux treats everything as a file, running a command which prints a file will create a tempory file and we can use ```diff``` on that to get the answer.  
```~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)``` gives us the answer.  

### Writing to Multiple Programs
```pwn.college{ITaoWiK9r0nXmZJNVL51YO5HQ1m.dBDO0UDL1gTN0czW}```

'>(command)' is process substitution, which creates named pipes that send the output directly to the command's input
Since we need to direct the output of '/challenge/hack' into both '/challenge/the' and '/challenge/planet' at the same time, we need to use process substitution  
```~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )```  
This will give us the output  

###  Split-piping stderr and stdout
```pwn.college{ctvlVK2qhFU2q-r2jQ5MVupE73w.dFDNwYDL1gTN0czW}```

We need to send stdout to '/challenge/planet' and stderr to '/challenge/the'  
```
~$ /challenge/hack | tee>(/challenge/planet) 2>&1 /challenge/the
Error-
ssh-entrypoint: tee/dev/fd/63: No such file or directory
Are you sure you're properly redirecting /challenge/hack's standard output into '/challenge/planet'?
You must redirect my standard error into '/challenge/the'!
```  
```
~$ /challenge/hack | tee>(/challenge/planet) | 2>&1 /challenge/the
Error- 
ssh-entrypoint: tee/dev/fd/63: No such file or directory
Are you sure you're properly redirecting /challenge/hack's standard output into '/challenge/planet'?
You must redirect my standard error into '/challenge/the'!
Are you sure you're properly redirecting /challenge/hack's standard error into '/challenge/the'?
```  
```
~$ /challenge/hack | ( /challenge/planet ) 2> >( /challenge/the )
Error- 
You must redirect my standard error into '/challenge/the'!
You are redirecting standard error *of /challenge/planet*! Instead, you must redirect standard error of 'hack'.
This must be done *before* any |. The right side of the pipe is a different command, with its own redirection, than the left side!
Are you sure you're properly redirecting /challenge/hack's standard error into '/challenge/the'?
```
Judging by the above error messages, one correction we need to make is that the standard error or 'hack' must be redirected before using | or | must not be used at all.  
This is probably because using | mixes the stdout and stderr.  
Lets try using a command without |  
For example-  

~$ echo hi | rev  
ih  
~$ echo hi > >(rev)  
ih  

The first and second programs are the same, hence lets try using the second method.  
```~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)```  
In this command, we are using > and 2> to split it into an stdout which goes into >(/challenge/planet) and an stderr which goes into >(/challenge/the)  
This gives us the flag.
