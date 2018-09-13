# XSS-game by Google
Google has created XSS interactive  game with 6 levels. [XSS-game](https://xss-game.appspot.com/ "XSS game area")

When you pass all the challenges, you will be rewarded with an appealing cake! 




## Level 1: Hello, world of XSS

In this level you will learn what happens to the application if you use input from user directly without proper escaping.   

In this level you will need to run a JavScript alert windows, to do so you will need to run alert from the FourOfFour search box.
We will run the following line from the search box,

```html
<script> alert() </script>
```

(We can put any message in the alert, like: `alert("WOW")` )  




## Level 2: Persistence is key

Thuis level is similar to level 1. But this time directly inserting `<script>` tag will not work. 
So, we will run an "invisible" javascript.  
We will run it from the new post box.

```html
<img src="demo" onerror='javascript:alert();' />
```

(Like level 1, we can put any message in the alert, like: `alert("Booooo")` )  





## Level 3: That sinking Feeling
There is no input field in thie level. But still Cross Site Scripting is possible via the address path as the JavaScript code directly uses `self.location.hash.substr(1)`. It is the url part after the `#` sign.
We will need to put the `alert()` inside the page URl like this:  

```javascript
http://xss-game.appspot.com/level3/frame#'onerror='alert()'
```

(Like previous levels, we can put any message in the alert, like: `alert("Ya Yi")` )  






## Level 4: Context matters
The code passes user value directly to `onload="startTimer('{{ timer }}');"` method. Thus we can exploit the script. 

We will put the following JavaScript in the input field

```javascript
');javascript:alert('Maverick
```

(Like previous levels, we can put any message in the alert, like we did with writing `Maverick` )  




## Level 5: Breaking protocol
This is the most tricky challenge.   
Here some templates are connected in chain by storing the `next` URL in a variable.  
So, if we can somehow change the value of `next` variable then XSS will work.

So we simply change the existing URL to the following URL:
 
```javascript
http://xss-game.appspot.com/level5/frame/signup?next=javascript:alert("Level 5")
```

After pasting the URL, press the `GO` button, which will change the page.  
Now we will press the `Next` button, and the `alert` will turn on.   
    
(Like previous levels, we can put any message in the alert, like we did with writing `Level 5` )  





## Level 6: Follow the rabbit
In this level, we will need to run a `JavaScript` file from the URL.  
We can host a simple JavaScript file that contain only `alert()`, and then to paste it in the existing URL after the `#` symbol.   
  
We can also "make" a JavaScript file in the URL that containe the `alert()`, Like this:


```html
http://xss-game.appspot.com/level6/frame#data:text/plain,alert('xss')
```

(Like previous levels, we can put any message in the alert, like we did with writing `xss` )  




## Done! You rock!
   After you succeed in all the levels, we will gate a page with this HTML cake
   
   ```html
                                                         -oooo:-                                                        
                                                        omhsoosho`                                                      
                                                        Ndo:``:oh-                                                      
                                                        dms+--+ym:                                                      
                                                        -ymhohdh+`                                                      
                                                         `N/`.s.                                                        
                                                          +:  +                                                         
                                                          --  :                                                         
                                                          --  o                                                         
                                                          ..  +                                                         
                                                          ::  s        ..`                                              
                                                .:sssso.  --  +     :syhhyo`                                            
                                ..::::.       `odhhyyhdd. ::  s    .mhhyhhdh.       -:...`                              
                               /dhhhhhhs     .odddhyhdddh+y:  my-syhdhhyhhddy/`   .odhyyhh:                             
                              yNdhyyoyhmo+::+ms/+++//++/odm:  NNmNd+///+++/+ody::omhyssyhdm-                            
                            -sddyyyyyyyoommmmmmdhyyyyyyhddd: `ddmdmdhyssyyhhmmNNNNdhyyyyyhmo-`                          
                        ``-omdyyyssys///shdddddddddmmdddhyy-``yhddddhhhhhdmmmmmmdd/oyssyyyyhmhss-`                      
                     `:ohhdmddhhyyyyyshddddhhyyyyyhddhhyo:-...--shhyysssyyhhdhhhddyyysyyyhdddmNNmyo.                    
                    /hNNmmd/:o+/////:`/osyhhyyys+syyhhyysysooossyyyyyooyyyyyyysyy+./oooooos/:ydNNmNmo.                  
                   +dNmmmmmhoo+///////oossshhyyyyyyyyssoossoosoosssyyyyyyyhsoyyyys/:-..--:/+sdddmmmNMy                  
                  `hNmmdmmdmddddhhhyhysso+.oyssssso-./o:-/+oo++oo--osoooooo..oyyhyyyyyyhhhyhdddmmdmNNN                  
                  `yNmNNhhdmdddhhhyyyyyyys:-......`./+++/:o++oo++/-````..::/+sysysyyyhsshhhydddmmmNNNN                  
                   sMNNNNNNmmdmdhhhhyyyyyyhhssssoo+oo/+//:/+//+:++++ooosyooyssosyyhhyhsshdhdmmNmNmmMMN                  
                   -NNNNNNhmNmdmmmdddddmhhhyyyyssys///+/:://////o+osoo+osoossosyhhdddh+omddmNNmmNmNMMN                  
                   oMNNNNNNNNdydNmmmmmdhydhhsoooodhydhsshys+soyooooosssyhyhymdhdhyddmmmdmNNNNNNmNNNMMM                  
                   yMMNNNMmmNdmmNNNNNNmh/sysyysyhyddmhhyhyhhddyyyhmddhhdmdddmmmdmmmmNNmmmNmNNNNmMNMMMM                  
                  .dMMNNMMNNNmNNNNNNmmNNhsddddNNdmhdmddyyhdhdhdddhdmhhdddhmddmmmNNNNNNNNNNNNNNNNMNMMMM                  
                  :NMMMNMMNMNhhmNNNNmdmNNmhddmdNmmmmmmddddNmdhdhddddmddmmmmmmNdNmdmmNNNmNNNNNdmMMMMMMM                  
                  -mMMMMMNNmNNmNNNNNNNNNNNdmmNmNmNmNmmNNmmNNdhddmmmmNmhhhyohNMNMNmmmmNdmNNMMMNNMMMMMMM                  
                  .dMMMMMMNNNMMMMMNNNNNMNmmmNNNmmmmNNdddmmNNNmmdNNmNNNmmNNNNNNNNNNNNNNNmNNNNNmNMMMMMMM                  
                  :NMMMMMMMMMMMMMMMNmmNMNNNNNNNmmNmNNNNmdmNNNNNNNmNNdmNNMMNMmNNNNNNMMNdmNNNMNmmMMMMMMM                  
                  :NNMMMMMMMMMMMMMMMMNNMNNMNNNMMMNNNNNNmNmdmmmNNNNNNmmNNNNNNNNNNMNNMMMNNNNMMNmMMMMNNMN                  
                  :NMMMNNMMMMMMMMMMMMMNNMMMMNMMMNmNNMNNNNNmhNMNNMNNNMMNMMMMMNNMMNNNMNMMMMNMMNNMMNMNMMM                  
                  `hMMMNdMNNMNNNNNMMNNNNMMMMMMMMNmNMMMMNNNNNNNdmmmMNMMMMMMNNMMNmdNMMNMNNNNMNmmNMNMMMMN                  
                   yMMMMNMMNMNmmNNNMNmddmMMNNNMNNNNNMMNNNNMNNNNNNNmNNNNNNNNNNNNNddNdmdmmNNMNNdMMMMMMMN                  
                   yMMMMNMNMMNNMMNNNNmdmmNMNNdhmMNNNNNNmNMMddddmNNNmNNMMNmNmmmmmNNmmmmNMMMMMMNNNMMMMMN                  
                   yNNNMMNNMMMMMMNNNNNMmmdNNNNNNNNNNNNmNNNNNmNmmNNNNNNNNNNNmNmNNNNNNNNNNNNNMMMNNMMMMMy                  
                   +MMMMMMMMMMMNNNNMMMNNNNmNNNMNMNNMNNmhdNNNNNmNNNmmNNNNNNNNNNNMMNNmNNNNNMNMNMMMMMMMN:                  
                    NMMMMNMMMMMMMNNNNNNdNMNNNNNNmNNNNNNNNNmmhNNNNmdNNNNNNNNNMMNNMNNNNNNNNNMMMMNNMMMNs`                  
                    -sdmNMNNMMMMMNNNNmmmmNNNMNmNMNNNNNNNMNmNNNNNNmmmdmNNNMNmmmmNMNNMNMmmNNMMMNMNmd+-`                   
                      `.ohNNMMNMMNMNNmdmNNNNNNmNMNNMNNNNmNNNmmmNmNMMNNMNNMMNNNNNNNNNNMMMMMMMNNho.`                      
                          :+hdNNNNNNNNNNNNNNmNNNNNNNMNNNmNNNNmMmmmNNNMNNNNNNNNMNNMMMMMNNmdds/-                          
                             `--:+shddmmNmmmmNNNNMNNNMNNNNNNNNNNMMNMMMNNNmNNNMNNNNdh++/-.`                              
                                     `--++osdddddddysNmmhshmmmmmNmddddddho/:++/---                                      
                                                    `-.-. .------.                                 

    
```
