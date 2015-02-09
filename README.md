# Q & A

<b>Potential User: </b> So what does this thingy of yours do then?

<b>Developer:</b> Well basically it will allow you to stream media from the Internet onto your TV.

<b>User: </b> So I'll be able to watch Youtube?

<b>Dev: </b> Yes.

<b>User: </b> Well um... that's very good but it's not exactly got me interested. Does it do anything else?

<b>Dev: </b> Well you'll also be able to play video and audio from websites like Vimeo, Facebook, SoundCloud and over [500 other sites](https://github.com/rg3/youtube-dl/blob/master/docs/supportedsites.md) directly on your TV.

<b>User: </b> That sounds promising but I mainly use my TV for watching - you know - just good old fashioned British TV programmes. 

<b>Dev: </b> You'll be able to watch those as well. Both BBC and ITV catchup services are supported as well as other TV services around the world.

<b>User: </b> OK now your talking - looks like I'll have more than enough choice to keep me entertained.

<b>Dev: </b> You can also play torrents.

<b>User :</b> Ah yes I have heard of those. Isn't that where you can download practically any movie, TV show or album?

<b>Dev: </b> Yes.

<b>User: </b> Well I've never actually done it myself - a friend of mine told me about it. He also said he has to decide beforehand what film he wants to watch so that he has time to download it - I'm afraid I'm not that organised.

<b>Dev: </b> You won't need to download it. Just pick a movie and it will start playing within about 60 seconds.

<b>User: </b> Great! but I also heard that it is, maybe, just a bit illegal?

<b>Dev: </b> Well, obviously, you need to check the law in your country and/or make sure you don't view any copyrighted material.

<b>User: </b> So basically your saying that I could potentially watch just about anything that's publically available on the Internet and all I need is one of those Raspberry Pi thingy-me-bobs?

<b>Dev: </b> Yes.

<b>User: </b> OK I'm sold. What do I need to do? Please don't tell it only runs on the command line and that I need to remember a load of switches.

<b>Dev: </b> Yes I'm afraid you'll need to use the command line - only joking! Everything can be controlled through a web app which you can use on your phone, tablet or PC. For all the other details read on... 

# PREREQUISITES

 - Raspberry Pi (Not model A) with at least 8Gb SD card running Raspbian. You should also have about 2 Gb of free space on the card.
 - Broadband connection with enough speed to support video streaming. Ideally you should have a wired ethernet connection into your Pi as some WiFi adapters may have problems with streaming.
 - Television plugged into Raspberry Pi.
 - Computer, tablet or smartphone for controlling server.

# INSTALLATION

To install you can either git clone this repository:

    git clone https://github.com/blissland/blissflixx.git

or download and extract the zip file:

    wget https://github.com/blissland/blissflixx/archive/master.zip
    unzip master.zip
    mv blissflixx-master blissflixx

Now enter the blissflixx folder and run the configure script which will install all the required external dependencies:

    cd blissflixx
    sudo ./configure.sh

It may take a while for this script to complete so now might be a good time to wash the dishes or take the dog for a walk.

# RUNNING THE SERVER

Hurray! the setup is now complete so you can start using the system. First start the server:

    ./blissflixx.py
    
Note that the first time you start the server it will first take a few moments to install the latest youtube-dl package.

Now open up a browser on your phone, tablet or PC and point it at:

    http://ip-address-of-your-pi:6969
    
So for example if the IP address of the Raspberry Pi is  192.168.1.4. Then you need to point your browser to:

    http://192.168.1.4:6969
    
If you want to run the server on the default port 80. Then you will need to start the server as root:

    sudo ./blissflixx.py --port 80
    
Finally if you want the server to continue running even after you log out of your session (which is usaully the case) then specify the --daemon flag:

    sudo ./blissflixx.py --port 80 --daemon
    
Fortunately there is script to run the above command:

    ./start.sh

# SUPPORTED MEDIA SITES

Blissflixx relies on youtube-dl for extracting media so a list of supported sites can be found on it's project site: https://github.com/rg3/youtube-dl/blob/master/docs/supportedsites.md

In addition BlissFlixx has support for ITV Player (https://www.itv.com/itvplayer/) which is not currently supported by youtube-dl.

# CREDITS

Blissflixx relies on the following projects to do all the heavy lifting:

 - youtube-dl for media extraction: https://github.com/rg3/youtube-dl
 - peerflix for torrent streaming: https://github.com/mafintosh/peerflix
 - omxplayer for media playback: https://github.com/popcornmix/omxplayer
