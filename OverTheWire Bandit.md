### Level 0-Level 1
```ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If```

The password is in a file called readme in the home directory so ```$ cat ~/readme``` will give us the password.  

### Level 1- Level 2
```263JGJPfgU6LtdEvgfWU1XP5yac29mFx```

Similar to previous question

### Level 2- Level 3
```MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx```

Similar to the previous question again, ```~$ cat ~/"spaces in this filename"``` will give us the password. 

### Level 3- Level 4
```2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ```

Similar to the previous levels but with a hidden file this time.  
```
~$ cd /inhere
~/inhere$ ls -al
~/inhere$ cat ...Hiding-From-You
```
Will get us the password.  

### Level 4- Level 5
```4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw```

We first need to do find the human readable file in 'inhere'.  
we can do that using- ```~$ file inhere/*```. This tells us that the file '-file07' is human readable.  
```~$ cat inhere/-file07``` will give us the password.  

### Level 5- Level 6
```HWasnPhtq9AVKe0dmk45nxy20cvUa6EG```

We can find the file using the 'find' command then then cat the contents.  
```
~$ find inhere/ -type f -size 1033c
~$ cat inhere/maybehere07/.file2
```  
Will give us the password.  

### Level 6- Level 7
```morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj```

Similar to previous one.  
```
$ find / -type f -size 33c -user bandit7
~$ cat /var/lib/dpkg/info/bandit7.password
```  
Will give us the flag

### Level 7- Level 8
```dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc```

A simple grep command ```~$ grep "millionth *" data.txt``` will give us the answer.  

### Level 8- Level 9
```4CKMh1JI91bUIZZPXDqGanal4xvAg0JM```

```~$ sort data.txt | uniq -u``` will give us the password.  
'the sort command is used to put duplicate text adjacent to each other and the uniq command will filter out the lines which occur more than once.  

### Level 9- Level 10
```FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey```

The 'strings' command is used to extract readable strings from a binary or unreadable file.
```~$ strings -a data.txt | grep "=*"``` will give us the password.  

### Level 10- Level 11
```dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr```

We can encode/decode base 64 data using the 'base64' command.  
```~$ base64 -d data.txt``` will give us the flag.

### Level 11- Level 12
```7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4```

We can use the tr command to solve this ROT13 cypher. The tr command is a UNIX command-line utility for translating or deleting characters.  
```~$ tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt``` will give us the flag.  
'A-Za-z' specifies the range of all uppercase and lowercase letters.  
'N-ZA-Mn-za-m' specifies how those letters should be rotated (shifted by 13 places)  

### Level 12- Level 13
```
