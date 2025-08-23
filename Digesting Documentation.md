### Learning from Documentation 
```pwn.college{Q-cF3dUEP49GWEk475xVP9FmCEz.dRjM5QDL1gTN0czW}```

The program for the challenge is '/challenge/challenge' and we need to pass it to the argument of '--giveflag'  
```~$ /challenge/challenge --giveflag```  
should give us the flag

### Learning complex Usage
```pwn.college{k-h3RqxkizvVuofSXkePyImd2og.dVjM5QDL1gTN0czW}```  

in this challenge the argument '--printfile' needs to be given another argument which is the path of the file it needs to print  
this works similar to the '-name' argument of the 'find' command  
```~$ >/challenge/challenge --printfile /flag```  
should give us the flag

### Reading Manuals
```pwn.college{o_jms6WcVBHMfP8URp5QUADjSDE.dRTM4QDL1gTN0czW}```  

the 'man' command will display the manual of the command we enter as an argument  
```~$ man challenge```  
this will open up the manual of the 'challenge' command  
```
CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)  

NAME  
       /challenge/challenge - print the flag!

SYNOPSIS  
       challenge OPTION

DESCRIPTION  
       Output the flag when called with the right arguments.

       --fortune  
              read a fortune  

       --version  
              output version information and exit

       --ojmscf NUM  
              print the flag if NUM is 685

AUTHOR  
       Written by Zardus.

REPORTING BUGS  
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO  
       man(1) bash-builtins(7)
```  
the manual tells about the '--ojmscf NUM' function which will give us the flag if NUM=685  
```~$ /challenge/challenge --ojmscf 685```  
will give us the flag

### Searching Manuals
```pwn.college{EF3QXhz-URlF672NgVg3Y5BPm7L.dVTM4QDL1gTN0czW}```

similar to the last challenge we need to check the manual of the command 'challenge'  
```~$ man challenge```  
we now need to search the entire manual for the right argument. we can search the manual by using '/'  
I used the command '/flag' to try to find the argument  
while going through the corresponding text i find  
```
--kjaysm  
              This argument will give you the flag!  
```
hence this will give us the flag-  
```~$ /challenge/challenge --kjaysm```  

### Searching for Manuals
```pwn.college{Az0TRseEFDtLwfDCbfw0L7Y-sEa.dZTM4QDL1gTN0czW}```  

```man man```  
This opens up the manual for the man page database  
On reading the manual we come across the following snippet-  
```
SYNOPSIS  
       man [man options] [[section] page ...] ...  
       man -k [apropos options] regexp ...  
       man -K [man options] [section] term ...  
       man -f [whatis options] page ...  
       man -l [man options] file ...  
       man -w|-W [man options] page ...  
```  
the 'man -k [apropos options]' command is the same as the 'apropos' command, hence it looked the most promising  
The apropos command is used to help users find any command using its man pages  
To know more- <u>https://www.geeksforgeeks.org/apropos-command-in-linux-with-examples/<u> 

```~$ man -k challenge```  
This gives us the output-  
```zsetwfbfws (1)       - print the flag!```  
'zsetwfbfws' is the name of the man page which gives us firther information about the challenge command  
```~$ man zsetwfbfws```  
This now gives us info about the function '--zsetwf NUM' which will print the flag if NUM is 007  
```~$ /challenge/challenge --zsetwf 007```  
will give us the flag  

### Helpful Programs
```pwn.college{I_aAlYPOxDvqMoDvwJB6pkNKIns.ddjM4QDL1gTN0czW}```  

the '--help' argument gives us the program's documentation  
```~$ /challenge/challenge --help```  
This tells us about a few arguments we didnt know of yet-  
```
optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
```
Now we need to find the value using the '-p' argument and then enter that in with the '-g' argument to get the flag  
```~$ /challenge/challenge -p```  
This gives us the value 641 to be used  
```~$ /challenge/challenge -g 641```  
this gives us the flag

### Help for Builtins  
```pwn.college{U7CtGbyMpztQwuDiASCZ_Qv-N2v.dRTM5QDL1gTN0czW}```  

since 'challenge' is a builtin not a command in this challenge, we can use the 'help' builtin to get some info on it  
```~$ help challenge```  
This gives us info of the function- '--secret VALUE' which will print the flag, if VALUE is correct.  It also gives us the right value (U7CtGbyM)  
```~$ challenge --secret U7CtGbyM``` should give us the flag

