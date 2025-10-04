### Launching Screen
```pwn.college{43zK_TqG5nRSbYd61loUuggNPdQ.QX1gjM4EDL1gTN0czW}```

```screen``` creates a virtual terminal inside your terminal that allows users to manage and switch between multiple terminal sessions within a single terminal window or SSH connection.  
For this problem, just opening the screen will give us the flag.  

### Detaching and Attaching
```pwn.college{oUkCdAAKF0mr1x6soG2kHSemAvv.QX2gjM4EDL1gTN0czW}```

We can keep the screen running in the background if we want. In this challenge, we need to use screen, detach from it, run /challenge/run and then reattach to get the flag.  

### Finding Sessions
```pwn.college{oaPn5RpQg5uGlnFbrl3btSXdeNH.QX3gjM4EDL1gTN0czW}```

We can choose which screen to attach to when there are multiple of them. 
```
~$ screen -ls
~$ screen -r 147
```
For this problem the screen with PID 147 gives us the flag.  

### Switching Windows
```pwn.college{kpSZwWn60SswYXhVARgPwpuJUUH.QX4gjM4EDL1gTN0czW}``` 

We first ```screen -ls``` to see the avaiable screens, we can then find and connect to windows 1 with its PID. After connecting to Windows 1, it asks us to use ```Ctrl-A 0``` to switch to windows 0.  
This gives us the flag.  

### Detaching and Attaching (tmux)
```pwn.college{kGBmJ4bSYLxyVctW1m2GL5WQAMT.QX5gjM4EDL1gTN0czW}```  

tmux (terminal multiplexer) is a modern alternative to screen. It works similarly to screen. 
For the purposes of this challenge, we need to launch tmux, detach from it run ```/challenge/run```, attach to the tmux and that will give us the flag. 

### Switching Windows (tmux)
```
