### Welcome to the Noomxffplayer github repo.

This is mostly here for information and tips on how to use ffmpeg's: ffplay as an alternative to omxplayer
and a lite comparison of the two.
*Omxplayer was forked and is being updated (outside offical raspios)*


### How does it(ffplay) work? 
From my understanding, ffmpeg leverages it using drm/mesa dri, v4l2 and probably sdl2.

### What is cool about using ffplay instead of omxplayer? 
  * It uses a standardized kernel drm method that works on 32/64bit arm/aarch64/x86_64 and maybe more.
  * omxplayer is just for 32bit versions(userland) of a raspberrypi with openmax headers.
  * You have full control over your console output with many options
  * It is included in offical repos
  * On the rpi platform you have alot of options to use with vc4-kms-v3d* overlay types, which won't work with omxplayer. 

### What is cool about using omxplayer instead of ffplay?
  * On the 32bit versions of raspberrypi with the 32bit userland and openmax headers, it can/will
  use less power and cpu cycles than ffmpeg/ffplay methods with drm.
  * Recent forks have been updated to build against newer ffmpeg versions and are very lightweight on cpu/memory use.
  * Recent forks have some interesting features, that have motivated me to soon build packages for bookworm/trixie    raspios 32bit
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
*COMING SOON* 




