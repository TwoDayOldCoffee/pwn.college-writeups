### cat: not the pet, but the command!
```pwn.college{8CvTZAEkD091RX3egDvcWdWgHZ9.dFzN1QDL1gTN0czW}```

the 'cat' command is used to read out the contents of a file <br>
cat flag <br>
since we need to find the flag and the 'flag' file is present in the 'home' directory already we can simply print it out using cat 

### catting absolute paths
```pwn.college{4k7chp5RwkG3uhmrm0xc0HZL13v.dlTM5QDL1gTN0czW}```

cat /flag<br>
This time we need to use the absolute path of the 'flag' file since its not present in the current directory (home)

### more catting practice
```pwn.college{EKDTOy4oIHGQqllZqwwmKEYJ1a3.dBjM5QDL1gTN0czW}```

In this challenge we cant use the 'cd' command and can only use the 'cat' command with the absolute path of the 'flag' file, however we dont know the absolute path of the 'flag' file<br>
if we run- 'cd /' then we get an error message saying:

--- you MUST chase pass 'cat' the absolute path of where I put it on the<br>
filesystem (which is /usr/share/apache2/flag).<br>
hacker@commands~more-catting-practice:

Hence we now have the absolute path of the 'flag' file and running-<br>
~$ cat /usr/share/apache2/flag      will give us the flag<br>

### grepping for a needle in a haystack
```pwn.college{AhuGGjnJ2I-MbYhPS_veMi5GSL-.ddTM4QDL1gTN0czW}```

since the data.txt file has too many lines of code to use 'cat' we can use 'grep' to only print out the lines of code we need, we can do this is the flag always starts with 'pwn.college'. The absolute path of the 'data' file has been given to us as '/challenge/data.txt'<br>

~$ grep pwn.college /challenge/data.txt<br>
the above statement will give us the flag

### listing files
```pwn.college{I1ZiE-8ft2mZ9A8U86ww54nPJeB.dhjM4QDL1gTN0czW}```

The 'ls' command lists out the contents of a directory<br>

running '~$ ls /challenge' give us the output-<br>
24592-renamed-run-28533  DESCRIPTION.md

hence '24592-renamed-run-28533' is the file we need to run-<br>
~$ /challenge/24592-renamed-run-28533 will give us the flag

### touching files
```pwn.college{QKG3XGNjpNfNBQtEuYfr-3MmOsj.dBzM4QDL1gTN0czW}```

the 'touch' command creates an empty file at the specified location.<br>
According to the question we need to create the file at two locations and then run '/challenge/run'

~$ touch /tmp/pwn
~$ touch /tmp/college
~$ /challenge/run<br>
will give us the flag

### removing files
```pwn.college{gU-YjQZV_uQdf6EtSF39OmKN-uy.dZTOwUDL1gTN0czW}```

the 'rm' command deletes a particular file<br>
the challenge wants us to delete the 'delete_me" file and run '/challenge/check' to check if its deleted

~$ rm delete_me<br>
~$ /challenge/check<br>
will give us the flag 

### moving files
```pwn.college{Qt1sRv8Il_urua0TdCYVhNkGlVI.QX5ETM3EDL1gTN0czW}```  

~$ mv /flag /tmp/hack-the-planet  
will move the /flag file into /tmp/hack-the-planet and then /challenge/run will give us the flag  

### hidden files
```pwn.college{IoPu-ozVmxNOce4b2UVn8gRHAyx.dBTN4QDL1gTN0czW}```

the ls command with the '-a' argument shows us all the files (including the hidden files in a directory)

~$ ls -a  /<br>
This shows us that the flag is saved in the '.flag-228627021295' file (hidden files always start with .)

:~$ cat /.flag-228627021295<br>
will give us the flag

### An Epic Filesystem Quest
```pwn.college{corSllxDhVI4xCKImannko7iwbk.dljM4QDL1gTN0czW}```

According to the challenge we need to find out the target file using ls, cd, cat<br>

~$ cd /<br>
/$ ls -a -al<br>
We execute the above two commands as we hv been asked to 

we then see a file names BLUEPRINT and so read its contents using '/$ cat BLUEPRINT'<br>
It reads out- <br>
"The next clue is in: /opt/linux/linux-5.4/drivers/staging/iio/adc<br>
Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!"

Since we cant cd into the directory, we do- <br>
/$ ls /opt/linux/linux-5.4/drivers/staging/iio/adc<br>
We can now see a file named 'CUE-TRAPPED' which we can read using '/$ cat /opt/linux/linux-5.4/drivers/staging/iio/adc/CUE-TRAPPED'<br>
this gives us the output-<br>
"The next clue is in: /usr/share/racket/pkgs/unix-socket-lib/racket/private<br>
The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'."

Since we need to enter the directory-<br>
/$ cd /usr/share/racket/pkgs/unix-socket-lib/racket/private<br>
/usr/share/racket/pkgs/unix-socket-lib/racket/private$ ls -a -al<br>
We can now see a file named 'TEASER' which we can read using ':/usr/share/racket/pkgs/unix-socket-lib/racket/private$ cat TEASER'<br>
this gives us the output- <br>
"The next clue is in: /usr/share/doc/liblzo2-2<br>
The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'."

/usr/share/racket/pkgs/unix-socket-lib/racket/private$ ls -a -al /usr/share/doc/liblzo2-2<br>
/usr/share/racket/pkgs/unix-socket-lib/racket/private$ cd /usr/share/doc/liblzo2-2<br>
We are now in the directory and can see a hidden file named '.POINTER' which we can read using '/usr/share/doc/liblzo2-2$ cat .POINTER'<br>
this gives us the output-<br>
"The next clue is in: /opt/libslub/.git/objects/f2<br>
Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!"

Since we cant enter the directory-<br>
/usr/share/doc/liblzo2-2$ ls /opt/libslub/.git/objects/f2<br>
we see a file named WHISPER-TRAPPED which we can read by using '/usr/share/doc/liblzo2-2$ cat /opt/libslub/.git/objects/f2/WHISPER-TRAPPED'<br>
this gives the output-<br>
"The next clue is in: /usr/share/icons/Adwaita/64x64/emblems<br>
The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'."

Since we hv to enter the directory-<br>
/usr/share/doc/liblzo2-2$ cd /usr/share/icons/Adwaita/64x64/emblems<br>
/usr/share/icons/Adwaita/64x64/emblems$ ls -a -al<br>
we see a file named SECRET which we can read using '/usr/share/icons/Adwaita/64x64/emblems$ cat SECRET'<br>
this gives the output- <br>
"The next clue is in: /opt/ghidra/Ghidra/Debug/Debugger-agent-dbgmodel-traceloader/lib"

/usr/share/icons/Adwaita/64x64/emblems$ ls -a -al /opt/ghidra/Ghidra/Debug/Debugger-agent-dbgmodel-traceloader/lib<br>
we see a file named BRIEF which we can read using- '/usr/share/icons/Adwaita/64x64/emblems$ cat /opt/ghidra/Ghidra/Debug/Debugger-agent-dbgmodel-traceloader/lib/BRIEF'<br>
this gives the output-<br>
"The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/TeX/AMS<br>
Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!"

Since we cant enter the directory-<br>
/usr/share/icons/Adwaita/64x64/emblems$ ls -a -al /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/TeX/AMS<br>
We see a file named ALERT-TRAPPED which we can read by using- '/usr/share/icons/Adwaita/64x64/emblems$ cat /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/TeX/AMS/ALERT-TRAPPED'<br>
this gives the output-<br>
"The next clue is in: /opt/aflplusplus/nyx_mode/QEMU-Nyx/include/hw/misc/macio"

:/usr/share/icons/Adwaita/64x64/emblems$ ls -a -al /opt/aflplusplus/nyx_mode/QEMU-Nyx/include/hw/misc/macio<br>
we see a file named INFO which we can read by using- '/usr/share/icons/Adwaita/64x64/emblems$ cat  /opt/aflplusplus/nyx_mode/QEMU-Nyx/include/hw/misc/macio/INFO' and this finally gives us the flag.

### making directories
```pwn.college{IkDWU0H9QZ41ymR7xxTaisgr2VA.dFzM4QDL1gTN0czW}```

the 'mkdir' command is used to create directories<br>
according to the challenge-

~$ mkdir /tmp/pwn<br>
~$ touch /tmp/pwn/college<br>
~$ /challenge/run<br>
will give us the flag

### finding files
```pwn.college{AkjQ9GAmNHOzSKSTYpeJV35AkhV.dJzM4QDL1gTN0czW}```

the 'find' command finds any file in any search location we want. <br>
The '-name' argument is used to specidy that we are searching for a file by its name 

~$ find / -name flag<br>
The above statement is searching for the 'flag' file by its name in the '/' directory

we get an output consisting of multiple files, some of whose permission is denied<br>
if we read out the contents of each permissible file (using cat) one by one we find that the '/usr/lib/jvm/java-11-openjdk-amd64/legal/jdk.zipfs/flag' file gives us the flag

### linking files
```pwn.college{UCmugkNegdH5esZnJFzXKF-HWYa.dlTM1UDL1gTN0czW}```

the 'ln' command with the '-s' argument created a symlink of a file

'/challenge/catflag' reads out '/home/hacker/not-the-flag' but we want it to run '/flag' to do this we need to create a symlink of '/flag' with '/home/hacker/not-the-flag' as the address file.<br>
However, running '~$ ln -s /flag /home/hacker/not-the-flag' immediately will give us an error message as that file already exists, hence to make it the symlink we need to delete the file first

rm /home/hacker/not-the-flag <br>
ln -s /flag /home/hacker/not-the-flag <br>
We hv now made symlink where '/flag' can be called by using '~/not-the-flag'

'~$ /challenge/catflag' will now run '/flag' and give us the flag as the output
