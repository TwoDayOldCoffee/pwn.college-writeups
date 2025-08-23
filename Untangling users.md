### Becoming root with su
```pwn.college{I4bsCL8naSI1wwhL4CjuNo1i4mE.dVTN0UDL1gTN0czW}```

The su command is an antiquated version of the sudo command which on running as root opens a root shell. To do this it needs a password.  
```
~$ su
Password:hack-the-planet
/home/hacker# cat /flag
```
Will give us the flag.

### Other users with su
```pwn.college{cpi2bfhjZRepf2v5C4SzEFT5KhL.dZTN0UDL1gTN0czW}```

We can also use su to switch to another user by gigivng that user's name as an argument.  
```
~$ su zardus
Password: dont-hack-me
/home/hacker$ /challenge/run
```
Will give us the flag

### Cracking Passwords
```pwn.college{E8bkHo3t4PFIkSywJi055YEVWo3.ddTN0UDL1gTN0czW}```  

John the Ripper is a password cracking tool in Linux and other operating systems. In this challenge we need to use john to ripper to crack the password, then su to zardus using the password we cracked and get the flag.  
```
:~$ john /challenge/shadow-leak
~$ john --show /challenge/shadow-leak

Output-  zardus:aardvark:20013:0:99999:7:::

~$ su zardus
Password: aardvark
~$ /challenge/run
```
Will give us the flag 

### Using sudo
```pwn.college{Q0-CXkOmFGi_uWaLfUMjEWnfnTB.dhTN0UDL1gTN0czW}```

Sudo is similar to su, but works differently in the way that unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root.  
```~$ sudo cat /flag```  
Will give us the flag.
