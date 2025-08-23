### The Root
```pwn.college{IjgyaMZu4cswN0grd5oZMRkrOkc.dhzN5QDL1gTN0czW}```

We need to execute the pwn program with the '/' root, '/pwn' should give us the flag

### Program and Absolute Paths
```pwn.college{kmYufFtXVjYQFkUhAqavfjKFq0d.dVDN1QDL1gTN0czW}``` 

we need to run the 'run' file in the 'challenge' directory with a '/' root,  hence '/challenge/run' will give us the flag

### Position thy self 
```pwn.college{coUuR2zPQ6cucelECu8Vud1F5NY.dZDN1QDL1gTN0czW}```

executing /challenge/run give give an error saying "You are not currently in /sys/kernel directory" <br>
cd /sys/kernel<br>
/challenge/run<br>
should give us the flag

### Position elsewhere
```pwn.college{EBaoitcH1A9UclPI76-BwA5IGqi.ddDN1QDL1gTN0czW}```

running /challenge/run will give the error- "Currently not in /home directory"<br>
cd /home<br>
/challenge/run<br>
will give the flag

### listing files
```pwn.college{I1ZiE-8ft2mZ9A8U86ww54nPJeB.dhjM4QDL1gTN0czW}```

The 'ls' command lists out the contents of a directory<br>

running '~$ ls /challenge' give us the output-<br><br>
24592-renamed-run-28533  DESCRIPTION.md

hence '24592-renamed-run-28533' is the file we need to run-<br>
~$ /challenge/24592-renamed-run-28533 will give us the flag

### implicit relative paths, from /
```pwn.college{IJo4bwsyx3avgN_k9VefbUoC6YK.dlDN1QDL1gTN0czW}```

since we need to run it using a relative path-<br>
cd /<br>
challenge/run

### Position yet elsewhere
```pwn.college{IAxnk_U6sK2iXa67aN3IdXzU7fy.dhDN1QDL1gTN0czW}```

running /challenge/run gives an error saying "Currently not in /home directory"<br>
cd /home<br>
/challenge/run<br>
should give the flag

### implicit relative path
```pwn.college{cUA6yyfE2rBjPCUb2McSAci4fPj.dFTN1QDL1gTN0czW}```

since we hv to run it from the /challenge directory- <br>
cd /challenge <br>
since we hv to run it using a relative path-<br>
./run

### home sweet home
```pwn.college{gkoNxMaORU05MyVSIq1L4te0Shv.dNzM4QDL1gTN0czW}```

since we need to copy it into a file who's path is lesser than 3 characters and no premade file we can create a file named 'a', (This needs to be done inside the /home/hacker directory)-<br>
touch a<br>
now we cna copy the contents of flag into a<br> 
/challenge/run ~/a<br>
This will give us the flag 
