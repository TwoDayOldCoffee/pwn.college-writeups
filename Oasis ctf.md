## Ready Player One
Its very noticeable that the audio file given is morse code and on putting it into an audio to morse code converter (https://morsecode.world/international/decoder/audio-decoder-adaptive.html) will give us the flag

## Arte-Miss?
Since the file is a picture, there are a few things that can be done-  
- We can check the properties of the file  
- It can involve converting the picture to hex
- etc.  

Lets check the properties of the picture first since its the simplest one-  
Tha flag is present as the Author's name under the Details tab  

## Jekylle and Hide!
The link opens up a website, since none of the elements on the website seem to be interactable, we can try inspecting the website for clues.  
On manually searching through the code, we find- half of the key is in 'book.js' and the other half is in 'script.js'  

## Keynough is enough
In this challenge we hc a cyher (KHAAH{W1C3J7_C1O3F3G3}) and key (WHISPER).  
Based on a cursory google search and the hint (consider a method that involves a repeating patternâ€”like adding a touch of vinegar) we can assume that this is a Vignere cypher.  
On putting it into an online decrypter, it gives us the flag.  

## BasiKELLY
A quick google search on the significance of the '====' at the end of the cypher tells us that its in base32 encoding. By putting it into on online decrypter, we can get the flag.  

## Knock Knock
The QR Code cant be used as is. However, we can put it into MS Paint and use the fill tool to make the qr code readable and this will give us the flag.  

## Microsoft Strongedge 
There are a few things we can try-
- Check its properties
- Check for embedded files
- Check for anything hidden in the ppt  
We can find a picture which has been madevery small hidden in the corner of the first slide with a cypher on it.
On using an online cypher decoder it gives us the flag

## Quence your Thirst
We see a large batch of nonsensinsical text.  
However one noticeable thing to our advantage is that we see (DLLWB://RGLM.QZ/TUZIOYPJ). This certainly is a hyperlink.  
Since we know the first 5 letters are 'https' this gives us an idea about 4 letters of the 26. Now lets look at the rest of the text after replacing these 4 letters that we know of.  
Say there is a word like "thx" (x is used as a placeholder here for an unknown letter and doesnt correspont to the letter 'x' itself). We can say with a reasonable degree of confidence that this word must be "the' and so 'x' mean 'e'.  
We can use this method to confidently get 22 out of the 26 letters.  
After putting the right letters into the hyperlink, we are left with 4 characters which we arent confident about.  
Taking into account the possible combinations, this leaves us with 24 unique hyperlinks and since 24 isnt high we can manually try all of them to get the flag in one of the links.  
