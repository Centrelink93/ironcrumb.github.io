---
layout: default
---
# SmoothBrain 4n6 - RDP Bitmap Cache

Lets say that youre a hacker and that you RDP into an organization's server. From this server, you then RDP into the domain controller based on stolen credentials. Other than event logs, how else can you get forensic artifacts? Well you can use RDP bitmap cache. 

Whats RDP bitmap tho?

Well lets say that you RDP into another computer. Wherever your mouse moves, a small 64x64 pixel image is saved to your local computer. Why? Because its easier to load a small 64x64 bitmap image from your local machine than it is to send a full 1920x1080 image from the remote machine to show you an updated portion of your connection. 

But the cool thing is, your mouse moves a LOT when you use RDP. And the cache can hold thousands of 64x64 bitmap images. With this in mind, one could theoretically reconstruct an entire desktop environment and see exactly what a threat actor can do. 

But where can I get the cache file? 

```
C:\Users\<user_account>\AppData\Local\Microsoft\Terminal Server Client\Cache\CacheXXX.bin
```
This is where some amazing tools can come into play:
bmc-tools.py 
RdpCacheStitcher

Note: RDP cache stitcher is kinda shit. I dont wanna put together a 6000 piece puzzle, so fuck that. 

Instead use bmc-tools.py.

Why? Because it parses out the bitmap cache file and results in a folder with all of its contained images as well as making a collage of them.

The collage can allow an analyst to see what a threat actor does. From here, you can see a threat actor run code in the command line, see what websites are visited, and more.  But the thing about the collage is it roughly shows where the mouse goes in order. At the top of the collage will likely show the first connection to the server, while the bottom of the collage can show the last moment of the RDP connection. 

But you'll also likely see some images which dont belong in the right place. It kind of resembles a serial killer note. It gives a portion of the picture, but not everything. This is why RdpCacheSticher exists. It exists for a user to solve a larger puzzle. You place each 64x64 bitmap image on the pane and AI is used to guess the next image to pair up to the current puzzle. In practice, the AI essentially does nothing. 

But how can one get meaningful information from these images without solving a thousand+ piece puzzle?

Three things: OCR, Colors, and Context

OCR, also known as Ocular Character Recognition, is a machine learning algorithm which takes an image and attempts to read discernable characters from it. Now, how can this happen with small 64x64 bitmap images? Well, that's another topic, but you can start to google from here. Using OCR, an Analyst can read each bitmap image. This is a step towards better analysis.

Color is also important. Each image has dominant colors. For example if you open a Windows command line window, on a green background, a bitmap image from the cache may consist of 70% commandline,  and 30% desktop. By using Python libraries like Pillow and OpenCV, one can determine the dominant color of each image. 

Using these two concepts, an analyst can create context. Using parsed characters and dominant colors, one can categorize text alongside a color as a commandline or powershell entry. 

This means an analyst can remove junk-like images from their analysis making specific aspects of the collage more clear. By doing so, an analyst can quickly ascertain bad things a threat actor may do.

There is no public software that provides the aforementioned features at this point in time. But it would be cool if someone made this ;)
