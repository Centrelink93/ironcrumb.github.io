# My Flipper Zero Tips & Tricks
<p align="center">
<img src="https://cdn.shopify.com/s/files/1/2175/8571/files/Flipper-Zero_1235x.png?v=1682525077"  width="600" height="500">
</p>
Recently I have obtained a Flipper Zero. Here I will share some useful resources as well as some things I have learned about this awesome little device!
The first thing I learned about is different firmware which can allow your flipper zero to do more things that are advertised. One major example of this is the "BadUSB" tool which is included with the flipper zero. The bad USB tool allows a threat actor to input their flipper zero device to another computer via a USB cable and then run rubber ducky scripts. However, utilizing [Xtreme firmware](https://github.com/ClaraCrazy/Flipper-Xtreme), one is able to wirelessly do these attacks over bluetooth. There is even potential to hijack old wireless keyboard dongles to do the same thing. Furthermore, the Xtreme firmware offers a lengthy list of really awesome features. 
These include the following:
* Installed games like tetris, solitare, and a tomogotchi
* Music apps
* Weather station scanning
* Spectrum analyzer
* WiFi hacking programs
* NSFW mode (NSFW screen savers)
* Better quick access menu
* And many many more
To install the Xtreme Firmware, click [here](https://github.com/ClaraCrazy/Flipper-Xtreme/releases/tag/XFW-0046_06052023), then be sure to plug in your flipper zero to your Windows computer, and click "Web Updater Chrome". This will install the firmware seamlessly!


Another thing I learned about is Marauder. This is an application which gets preinstalled with the Xtreme Firmware which allows a threat actor to scan for wireless access points, then run attacks against them. These attacks can include deauthing attacks as well as rickrolling attacks. **However, it is not clearly mentioned that Marauder requires a firmware/BIOS configuration for the Flipper WiFi development board.** With this in mind, I suggest you watch the [following video](https://www.youtube.com/watch?v=CabgV-ljjRM) in order to configure the dev board properly. This will allow you to use the WiFi marauder application properly.





