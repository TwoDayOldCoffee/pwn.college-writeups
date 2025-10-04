### The PATH Variable
```pwn.college{IWzRTi3jQTK-uXgNJwccu5oeOJb.dZzNwUDL1gTN0czW}```  

Disrupting the PATH variable is enough to give us the answer to this chalenge.  
```
~$ PATH=""
:~$ /challenge/run
```
Will give us the flag

### Setting Path
```pwn.college{Y6QzWTpIyFISDHJLA2HZI9HxETM.dVzNyUDL1gTN0czW}```

The PATH variable can also be given a value to help us run a command just by its name.  
```
~$ PATH=/challenge/more_commands/
~$ /challenge/run
```
Will give us the flag

### Finding Commands
```pwn.college{YunbB9Kk1NvKb914yJaYdZJWJ-h.QX3MTM3EDL1gTN0czW}```

```which``` can be used to find the file address. we can use this to find the flag file in this challenge.  
```
~$ which win
/challenge/paths/13177/win
~$ cat /challenge/paths/13177/flag
```

### Adding Commands
```pwn.college{QdcfJ91hON5f-H-sBzyJ7sdSj1p.dZzNyUDL1gTN0czW}```

```
~$ touch win
~$ chmod +x win
~$ nano win
```  
We add ```/usr/bin/cat  /flag``` inside the shell  
```
:~$ PATH=/home/hacker
~$ /challenge/run
```
Will give us the flag  

### Hijaking Commands
```pwn.college{4teuNBX08yC4pqiN2zltzQgqu54.ddzNyUDL1gTN0czW}``` 

In this challenge, we need to trick /challenge/run into printing the flag by changing the rm comamnd.  
```~$ nano rm```
In the shell we add- ``` read FLAG < /flag; echo $FLAG```  
```
chmod o+x rm
~$ PATH=~/
:~$ /challenge/run
```
Will give us the flag

