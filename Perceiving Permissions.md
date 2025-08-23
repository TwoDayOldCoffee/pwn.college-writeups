### Changing File Ownership
```pwn.college{E8OLWY_Una9o-tRLkXjkQGrjvlV.dFTM2QDL1gTN0czW}```

The flag file can only be read as the root user and so if we are to read out the contents of it, then we need to get 'hacker' to be considered as the user.  
To do this we can use the chown command which changes the user of a file. (typically this can only be used by the root user but for the purposes of this challenge we can use it as hacker)  
```
~$ chown hacker /flag
~$ cat /flag
```
will give us the flag

### Groups and Files
```pwn.college{ss_f5bBUmApNc6WrxklAaiuysJZ.dFzNyUDL1gTN0czW}```

Similar to the previous question, in this challenge we can change the group of the 'flag' file to 'hacker' in order get permission to read it out.  
```
~$ chgrp hacker /flag
~$ cat /flag
```
Will give us the flag

### Fun with group names
```pwn.college{U9L-L5AZ9lJ0nHJsBJF8YjXt3Gj.dJzNyUDL1gTN0czW}```

We need to change the group of the flag file to the group of the user. We can find the group of the user using the 'id' command.  
Using the id command gives us the output- ```uid=1000(hacker) gid=1000(grp24040) groups=1000(grp24040)```  
```
~$ chgrp grp24040 /flag
~$ cat /flag
```
Will give us the flag

### Changing Permissions 
```pwn.college{Eo3yvty1366PlBKPRNAzDMR0gSL.dNzNyUDL1gTN0czW}```

We can use the 'chmod' command to change the permissions of the files we want.  
For the purposes of this challenge we need to change the permissions of the flag file to be read by the public (Since hacker isnt a user nor a part of the group).  
```
~$ chmod o+r /flag 
~$ cat /flag
```
Will give us the flag

### Executable Files
```pwn.college{UKY9iCdfQ_k364BZ1I56q9mwINf.dJTM2QDL1gTN0czW}```

Similar to the previous question but here we need to make the program to be excutable.  
```
~$ chmod a+x /challenge/run
~$ /challenge/run
```
Will give us the flag

### Permission Tweaking Practice
```pwn.college{kItLqfRiswcsBAY2LzEQLwG_VZz.dBTM2QDL1gTN0czW}```  

In this program we will be given a set of 8 changes to be made to the /challenge/pwn file in order to unlock chmod permission for the '/flag' file.  
The 8 changes to be made in order are-  
```
~$ chmod o-r /challenge/pwn
~$ chmod u+x /challenge/pwn
~$ chmod o+rx /challenge/pwn
~$ chmod uo-rwx /challenge/pwn
~$ chmod o+r /challenge/pwn
~$ chmod o+wx /challenge/pwn
~$ chmod g+w /challenge/pwn
~$ chmod u+wx /challenge/pwn
```
We can now chmod the flag file  
```
~$ chmod a+r /flag
~$ cat /flag
```
Will give us the flag 

### Permissions Setting Practice
```pwn.college{Ip6F6MvRSfGUYSSek2VZp5rjBFg.dNTM5QDL1gTN0czW}```

This challenge is the same as the previous one but we need to use =.  
= helps us set permissions altogether instead of updating the old ones.

### The SUID Bit
```pwn.college{Ydg_VVj8ngo-Ne64gpkGNJ16SBA.dNTM2QDL1gTN0czW}```

The SUID Command gives a user temporary elevated access to do certain tasks. We can use this to get the flag in this challenge.  
```
~$ chmod a+s /challenge/getroot
~$ /challenge/getroot
~# cat /flag
```
Will give us the flag.  







