## Section 1: Preparing the Application

Step 1. Download Popcorn TV or Clone the Repository. For ease of updating I suggest that you clone the repository, if you do not know how to do that then please follow this [guide.](https://github.com/OstlerDev/PopcornTV/wiki/How-to-Clone-the-Project)  
Step 2. Drag PopcornTV to your desktop (and extract it if you downloaded the zip). Rename it "PopcornTV".  
Step 3. Open Terminal and enter the commands below.
```sh
$ cd Desktop
$ cd PopcornTV
$ sudo npm install
$ sudo node atv.js
```
Step 4. On the first run it will generate the certificates needed to run the application, once those are generated restart the program again using the following command.
```sh
$ sudo node atv.js
```
Step 5. It will create a file named "config.json" and auto fill it with your local IP.
Step 6. Run the program again. If you see something like below then you are ready to move on.
```
Starting PopcornTV
DnsProxy binding on 10.0.1.2:53
Web: listening on 10.0.1.2:80
SSL Web: listening on 10.0.1.2:443
```

## Section 2: Preparing your Apple TV

Step 1. Go to your Apple TV and select the settings Application.  
Step 2. Select General > Network > "Your Network" > "Your network" again. You should end on a page that says "Wifi Configuration" at the top. (It might also say "Ethernet Configuration", this is normal and OK)  
Step 3. Go down to "Configure DNS" and set it to Manual, then enter in the local IP address of your Computer that is running PopcornTV. In my case it was "10.0.1.2". (You will see that the DNS setting has 3 spaces for each section, for me since my IP is "10.0.1.2", I would put "010.000.001.002" in the spaces, just add zeros where needed.)  
Step 4. Once the DNS is set, menu out back to the "General" page.  
Step 5. Scroll down to where it says "Send Data to Apple" and select it then set it to "No"  
Step 6. Once your setting says "No", while hovering over "Send Data to Apple" (like shown in the image below) press the "Play/Pause" button on your Apple TV remote. It will open up a screen that we will use in the next window.  
![](http://i.imgur.com/ZUwdFkq.jpg)
Step 7. Select "Add Profile" then click "Ok"  
Step 8. On the "Add Profile" page it should pull up a text box. Type in "http://trailers.apple.com/trailers.cer" then click "Submit". This adds a custom profile to your Apple TV that allows SSL connections between your Apple TV and the PopcornTV Application.  

## Section 3: Wrapping Up

You are now done with the installation! Just make sure PopcornTV is running whenever you wish to use it!

PopcornTV runs inside the Trailers application on your Apple TV. Just open the trailers application to begin.