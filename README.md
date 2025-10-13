### Welcome to the Noomxffplayer github repo.

No more omxplayer but ffplay works :)

This is mostly here for information and tips on how to move away from omxplayer using ffmpeg's: ffplay.

Using FFmpeg/ffplay one can achieve full freedom away from omxplayer(if you haven't long ago already) and ensure updates will be coming.

### How does it work? 
From my understanding, ffmpeg leverages it using drm/mesa dri and probably sdl2.

* What is great about it, is that it will work on all most hardware using the same method.

* What else is cool about using ffplay instead of omxplayer? 
  *You still have control over your console, you can actually quit the application even if its running under systemd.*

### How can you make this work on your distro or build?

* Make sure your ffmpeg has been built with drm/sdl/v4l2 and all the parts needed. DietPi has it, I assume most debians have it built in. I've tested it
  on Rocky/Alma, they work too with the ffmpeg builds available from their external repos. Just note that unlike on Debian based setups, the rpm builds
  don't always include all the mesa3d bits needed for arm and other hardware.
  
* For the rpi's try using the vc4 for your board in config.txt
   dtoverlay=vc4-kms-v3d

    *I found reduced cpu use using the v4l interface as well

 *On a old rpi2 I'm currently testing it with:
 <code>
ffplay -an -codec:v h264_v4l2m2m -probesize 32 -sync ext rtsp://user:pwd@cameraip:port
  </codes>
**Seems to work well with acceptable CPU use, load avgs are down 50% over not specifying v4l2, I'm averaging < 1.0 now vs nearly 2 before on a rpi2.**
I do get artifacting but I think i need to tune the -probesize a bit more.
  

* For generic x86_64, it should just work once you have installed everything.
* Install ffmpeg and egl and mesa drivers for your hardware, then test connection to a camera or stream.
* Then you can start up automatically in a kiosk either using systemd or a shell script. Systemd is easier because it will manage the restarts if needed
and you can run it as a specific user easy as well,  I think you just need to make sure they are a member of the video group, maybe audio,input too.
*On Debian a quick method could be to install kmscube, then make sure it works, then test your camera/stream.*
GL and enjoy!
*I might upload an example systemd unit soon.*

This is so easy to do. 

### Downsides?
* Using non omxplayer options do use more CPU, but its not too bad. It will be more of a load on the oldest RPI's, but v4l2 helps a lot in those cases.

*I might build a version for this repo that is lean and tuned for the rpi0/0w that will come with a systemd template pre-setup with example usage.*




