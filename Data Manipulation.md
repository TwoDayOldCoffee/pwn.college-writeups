### Translating Characters
```pwn.college{sbrM5iKYM9A4OZZyZVt_0FSHzd9.QXzETM3EDL1gTN0czW}```  

Since we need to swap the case of the flag with ``tr``. ```~$ /challenge/run | tr  ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ``` will help us do that.  

### Deleting Characters
```pwn.college{USxugbeNQwBwoYJaF8hXoAZQikC.QX0ETM3EDL1gTN0czW}```  

```-d``` helps us delete characters with the ```tr``` command.  
```~$ /challenge/run | tr -d ^%``` will give us the flag.  

### Deleting Newlines 
```pwn.college{kfAEj3A8T8_R-BYXr0imrJTXZfe.QX1ETM3EDL1gTN0czW}```  

In this challenge, we need to remove the newlines from the flag so ```~$ /challenge/run | tr -d "\n"``` will give us the flag.  

### Extracting the First Lines with Head
```pwn.college{kBgMLS4bThaBgQFbcrkiINZyBet.QX2ETM3EDL1gTN0czW}```  

We can extract the first n lines using ```head```. In this challenge we need to use that to pipe the first 7 lines into ```/challenge/college```.  
```~$ /challenge/pwn | head -n 7 | /challenge/college``` will give us the flag.  

### Extracting Specfic Sections of Text
```pwn.college{o9uJ4n6VfWROIuMfM272p8RdZFG.QX3ETM3EDL1gTN0czW}```  

On running ```/challenge/run```, we can see that the contents of the flag are in the second column. We can use ```cut -d " " -f 2 ``` to extract only the second column and ```tr -d "\n"``` to get them together as one string.  
```~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"``` will give us the flag.  

### Sorting Data
```pwn.college{8FKRnO2aQW3tQHe6vyUhl4Qej0J.QXwQzM4EDL1gTN0czW}```

We can sort data using the ```sort``` command instead of ```cat```. Since we want the flag which is at the end, we can use the ```-r``` argument which prints in reverse order.  
```~$ sort /challenge/flags.txt -r``` will give us the flag.  
