### Matching with *  
```pwn.college{gU19m9Nk4Ov5bzzeT64QGYeXQkK.dFjM4QDL1gTN0czW}```  

the glob '*' will be used in this challenge.  
when the shell encounters the '*' glob it treats it as a wildcard and will replace that argument with any file that mathces the pattern  
for example if we give it the argument '/ch*', then all files starting with 'ch' will be taken  
```
~$ cd /ch*
/challenge$ /challenge/run
```  

the shell cd'ed to the 'challenge folder since we gave the argument '/ch*' and we ran the progam from there which gave us the flag  

### Matching with ?
```pwn.college{4XyNkBoepyl8BQz1p5TDwQEZLhR.dJjM4QDL1gTN0czW}```  

In this challenge we use the '?' glob which works similar to the '*' glob but only matches one character  
```
~$ cd /?ha??enge  
$ /challenge/run  
```
This will give us the flag

### Matching with []
```pwn.college{8i2FCALviTsygZPTvB7sas2batv.dNjM4QDL1gTN0czW}```

the [] will match the character with any of the characters given inside the brackets.  
```
~$ cd /challenge/files
/challenge/files$ /challenge/run file_[bash]
```  
since we had to run /challenge/run with an argument that bracket-globs into file_b, file_a, file_s, and file_h, we can write it this way and this will give us our flag. 

### Matching paths with []
```pwn.college{0UQhPEVQPvWANtva9R7mWYhU_qd.dRjM4QDL1gTN0czW}```  

Since globbing happens on a path basis, we can use the globs in our path arguments too.
```
~$ /challenge/run /challenge/files/file_[bash]
```  
Since we need to run the program from our home directory, while needing to file glob the files, we can give it the argument- '/challenge/files/file_[bash]' and this will give us our flag

### Mixing Globs
```pwn.college{kuCdYER7_KjCFGWTq4oveFAz9US.dVjM4QDL1gTN0czW}```  

We need to match the files- "challenging", "educational", "pwing"  
The only common characters in all 3 files are 'i' and 'n'  
on running the 'ls' command we find that the files in '/challenge/files' are-  
amazing,beautiful,challenging,delightful,educational,fantastic,great,happy,incredible,jovial,kind,laughing,magical,nice,optimistic,pwning,queenly,radiant,splendid,thrilling,uplifting,victorious,wonderful,xenial,youthful,zesty  

Since all of the file names start with a different letter and we need to run the files "challenging", "educational", "pwing", we can use the argument '[pec]*', this argument will use all the files starting with p,e or c  
```
~$ cd /challenge/files
$ /challenge/run [cep]*
```
will give us the flag

### Exclusionary Globbing
```pwn.college{skmoNB4fB3u8rWbW7o3PJ9DLCTN.dZjM4QDL1gTN0czW}```

the ^ character in [] will invert the functionality of the glob and use the files which dont have the characters entered, since we need to use the files not starting with p,w,n, our argument will be- [^pwn]*  
```
~$ cd /challenge/files
/challenge/files$ /challenge/run [^pwn]*
```
will give us the flag
