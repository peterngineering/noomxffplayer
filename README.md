### Welcome to the Noomxffplayer github repo.

This is mostly here for information and tips on how to use ffmpeg's: ffplay on 64bit systems.
*Including a lite comparison of omxplayer vs ffplay.
*Omxplayer was forked and is being updated (outside offical raspios)*


### How does it(ffplay) work? 
From my understanding, ffmpeg leverages it using drm/mesa dri
### What is cool about using ffplay instead of omxplayer? 
  * It uses a standardized kernel drm method that works on 32/64bit arm/aarch64/x86_64 and maybe more.
  * omxplayer is just for 32bit versions(userland) of a raspberrypi with openmax libs/headers.
  * Works with many/most file types/media sources, omxplayer needs a license for mpeg2 sources.
  * You have full control over your console output with many options.
  * It is very stable software(less bugs) and probably will not need a lot of process oversight management/recovery routines.
  * It is included in offical repos
  * On the rpi platform you have alot of options to use with vc4-kms-v3d* overlay types, which won't work with omxplayer. 

### What is cool about using omxplayer instead of ffplay?
  * On the 32bit versions of raspberrypi with the 32bit userland and openmax libs/headers, it can/will
  use less power and cpu cycles than ffmpeg/ffplay methods with drm on media sources it supports.
  * Works for sources that are compatible with its hardware/gpu videocore unit like h264/mjpeg.
  * With some process oversight(routine periodic restarts), it can work well even over wifi.
  * Recent forks have been updated to build against newer ffmpeg versions and are very lightweight on cpu/memory use.
  * Recent forks have some interesting and useful features.
  * On older hardware rpi's omxplayer can playback videoloops/music from playlists like an appliance.
    
### How can you make ffplay work on your distro or build?

* Make sure your ffmpeg has been built with drm/sdl/v4l2 and all the parts needed. DietPi has it, I assume most debians have it built in. I've tested it   on Rocky/Alma, they work too with the ffmpeg builds available from their external repos. Just note that unlike on Debian based setups, the rpm builds
  don't always include all the mesa3d bits needed for arm and other hardware.
  
* For the rpi's try using the vc4 for your board in config.txt
  
   <code>dtoverlay=vc4-kms-v3d</code>

 * I found reduced cpu use using the v4l interface as well
 * On a old rpi2 I'm currently testing it with:
 <code>
ffplay -an -codec:v h264_v4l2m2m -probesize 32 -sync ext rtsp://user:pwd@cameraip:port
  </codes>
**Seems to work well with acceptable CPU use, load avgs are down 50% over not specifying v4l2, I'm averaging < 1.0 now(displaying 720p is even less) vs nearly 2 before on a rpi2. This is not near as low as omxplayer can manage on
a rpi*
I do get artifacting but I think i need to tune the -probesize a bit more.
 
* For generic x86_64, it should just work once you have installed everything.
* Install ffmpeg and egl and mesa drivers for your hardware, then test connection to a camera or stream.
* Then you can start up automatically in a kiosk either using systemd or a shell script. Systemd is easier because it will manage the restarts if needed
and you can run it as a specific user easy as well,  I think you just need to make sure they are a member of the video group, maybe audio,input too.
*On Debian a quick method could be to install kmscube, then make sure it works, then test your camera/stream.*
GL and enjoy!

### How can you make omxplayer work on your rpi/32bit distro or build?


* I use linux as my primary OS. However, I'm very flexible and tolerant and like other OS's and even non GNU software too.

For a long time I had thought omxplayer was done. Well it was only really done in offical debian/raspios and a few more linux vendor repos.
I understand and know quite about about the linux kernel open drm standard linux replacement. I'm not downplaying it at all, but It is
nice that omxplayer is still around. I haven't tried it 'yet' , but I suspect the omxplayer from mjfwalsh being updated will work on non linux too.



See:
 https://github.com/mjfwalsh/omxplayer:
 
 He has been working on omxplayer for years and is still keeping it updated against newer ffmpeg releases.
 This likely means you can make/keep an omxplayer version working for sometime to come.
 The improvements he has made are quite impressive. 


I created my own'omxplayer' repo at:
The one I have a forked has included instructions for building on debian/raspios bookworm and a couple non posix changes specific to linux.
https://github.com/peterngineering/omxplayer/tree/bookworm

 

